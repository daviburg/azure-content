<properties 
	pageTitle="How to create and manage Azure Redis Cache using the Azure Command-Line Interface (Azure CLI)" 
	description="Learn how to install the Azure CLI on any platform, how to use it to connect to your Azure account, and how to create and manage a Redis cache from the Azure CLI." 
	services="redis-cache" 
	documentationCenter="" 
	authors="steved0x" 
	manager="dwrede" 
	editor=""/>

<tags 
	ms.service="cache" 
	ms.workload="tbd" 
	ms.tgt_pltfrm="cache-redis" 
	ms.devlang="na" 
	ms.topic="article" 
	ms.date="09/16/2015" 
	ms.author="sdanie"/>

# How to create and manage Azure Redis Cache using the Azure Command-Line Interface (Azure CLI)

The Azure CLI is a great way to manage your Azure infrastructure from any platform. This article shows you how to create and manage your Azure Redis Cache instances using the Azure CLI.

## Prerequisites

To create and manage Azure Redis Cache instances using Azure CLI, you must complete the following steps.

-	You must have an Azure account. If you don't have one, you can create a [free trial account](http://azure.microsoft.com/pricing/free-trial/) in just a few moments.
-	[Install the Azure CLI](../xplat-cli.md#install).
-	Connect your Azure CLI installation with a personal Azure account, or with a work or school Azure account, and log in from the Azure CLI using the `azure login` command. To understand the differences and choose, see [How to connect to your Azure subscription](../xplat-cli.md#configure).
-	Before running any of the following commands, switch the Azure CLI into Resource Manager mode by running the following command.
	`azure config mode arm`
	For more information, see [Setting the Azure Resource Manager mode](../virtual-machines/xplat-cli-azure-resource-manager.md#setting-the-azure-resource-manager-mode).

## Redis Cache properties

The following properties are used when creating and updating Redis Cache instances.

| Property         | Switch                    | Description                                                                                                                                  |
|------------------|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| name             | -n, --name                | Name of the Redis Cache.                                                                                                                     |
| resource group   | -g, --resource-group      | Name of the Resource Group.                                                                                                                  |
| location         | -l, --location            | Location to create cache.                                                                                                                    |
| size             | -z, --size                | Size of the Redis Cache. Valid values: [C0, C1, C2, C3, C4, C5, C6]                                                                          |
| sku              | -x, --sku                 | Redis SKU. Should be one of : [Basic, Standard]                                                                                              |
| MaxMemoryPolicy  | -m, --max-memory-policy   | MaxMemoryPolicy property of the Redis Cache. Valid values: [AllKeysLRU, AllKeysRandom, NoEviction, VolatileLRU, VolatileRandom, VolatileTTL] |
| EnableNonSslPort | -e, --enable-non-ssl-port | EnableNonSslPort property of the Redis Cache. Add this flag if you want to enable the Non SSL Port for your cache                            |
| subscription     | -s, --subscription        | The subscription identifier.                                                                                                                 |
| key type         | -t, --key-type            | Type of key to renew. Valid values: [Primary, Secondary]                                                                                     |

## See all Redis Cache commands

To see all Redis Cache commands and their parameters, use the `azure rediscache -h` command.

	C:\>azure rediscache -h
	help:    Commands to manage your Azure Redis Cache(s)
	help:
	help:    Create a Redis Cache
	help:      rediscache create [--name <name> --resource-group <resource-group> --location <location> [options]]
	help:
	help:    Delete an existing Redis Cache
	help:      rediscache delete [--name <name> --resource-group <resource-group> ]
	help:
	help:    List all Redis Caches within your Subscription or Resource Group
	help:      rediscache list [options]
	help:
	help:    Show properties of an existing Redis Cache
	help:      rediscache show [--name <name> --resource-group <resource-group>]
	help:
	help:    Change settings of an existing Redis Cache
	help:      rediscache set [--name <name> --resource-group <resource-group> --max-memory-policy <max-memory-policy>]
	help:
	help:    Renew the authentication key for an existing Redis Cache
	help:      rediscache renew-key [--name <name> --resource-group <resource-group> ]
	help:
	help:    Lists Primary and Secondary key of an existing Redis Cache
	help:      rediscache list-keys [--name <name> --resource-group <resource-group>]
	help:
	help:    Options:
	help:      -h, --help  output usage information
	help:
	help:    Current Mode: arm (Azure Resource Management)

## Create a Redis Cache

To create a Redis Cache, use the following command:

	azure rediscache create [--name <name> --resource-group <resource-group> --location <location> [options]]

For more information about this command, run the `azure rediscache create -h` command.

	C:\>azure rediscache create -h
	help:    Create a Redis Cache
	help:
	help:    Usage: rediscache create [--name <name> --resource-group <resource-group> --location <location> [options]]
	help:
	help:    Options:
	help:      -h, --help                                   output usage information
	help:      -v, --verbose                                use verbose output
	help:      -vv                                          more verbose with debug output
	help:      --json                                       use json output
	help:      -n, --name <name>                            Name of the Redis Cache.
	help:      -g, --resource-group <resource-group>        Name of the Resource Group
	help:      -l, --location <location>                    Location to create cache.
	help:      -z, --size <size>                            Size of the Redis Cache. Valid values: [C0, C1, C2, C3, C4, C5, C6]
	help:      -x, --sku <sku>                              Redis SKU. Should be one of : [Basic, Standard]
	help:      -m, --max-memory-policy <max-memory-policy>  MaxMemoryPolicy property of the Redis Cache. Valid values: [AllKeysLRU, AllKeysRandom, NoEviction, VolatileLRU, VolatileRandom, VolatileTTL]
	help:      -e, --enable-non-ssl-port                    EnableNonSslPort property of the Redis Cache. Add this flag if you want to enable the Non SSL Port for your cache
	help:      -s, --subscription <id>                      the subscription identifier
	help:
	help:    Current Mode: arm (Azure Resource Management)

## Delete an existing Redis Cache

To delete a Redis Cache, use the following command:

	azure rediscache delete [--name <name> --resource-group <resource-group> ]

For more information about this command, run the `azure rediscache delete -h` command.

	C:\>azure rediscache delete -h
	help:    Delete an existing Redis Cache
	help:
	help:    Usage: rediscache delete [--name <name> --resource-group <resource-group> ]
	help:
	help:    Options:
	help:      -h, --help                             output usage information
	help:      -v, --verbose                          use verbose output
	help:      -vv                                    more verbose with debug output
	help:      --json                                 use json output
	help:      -n, --name <name>                      Name of the Redis Cache.
	help:      -g, --resource-group <resource-group>  Name of the Resource Group under which the cache exists
	help:      -s, --subscription <subscription>      the subscription identifier
	help:
	help:    Current Mode: arm (Azure Resource Management)

## List all Redis Caches within your Subscription or Resource Group

To list all Redis Caches within your Subscription or Resource Group, use the following command:

	azure rediscache list [options]

For more information about this command, run the `azure rediscache list -h` command.

	C:\>azure rediscache list -h
	help:    List all Redis Caches within your Subscription or Resource Group
	help:
	help:    Usage: rediscache list [options]
	help:
	help:    Options:
	help:      -h, --help                             output usage information
	help:      -v, --verbose                          use verbose output
	help:      -vv                                    more verbose with debug output
	help:      --json                                 use json output
	help:      -g, --resource-group <resource-group>  Name of the Resource Group
	help:      -s, --subscription <subscription>      the subscription identifier
	help:
	help:    Current Mode: arm (Azure Resource Management)

## Show properties of an existing Redis Cache

To show properties of an existing Redis Cache, use the following command:

	azure rediscache show [--name <name> --resource-group <resource-group>]

For more information about this command, run the `azure rediscache show -h` command.

	C:\>azure rediscache show -h
	help:    Show properties of an existing Redis Cache
	help:
	help:    Usage: rediscache show [--name <name> --resource-group <resource-group>]
	help:
	help:    Options:
	help:      -h, --help                             output usage information
	help:      -v, --verbose                          use verbose output
	help:      -vv                                    more verbose with debug output
	help:      --json                                 use json output
	help:      -n, --name <name>                      Name of the Redis Cache.
	help:      -g, --resource-group <resource-group>  Name of the Resource Group
	help:      -s, --subscription <subscription>      the subscription identifier
	help:
	help:    Current Mode: arm (Azure Resource Management)

## Change settings of an existing Redis Cache

To change settings of an existing Redis Cache, use the following command:

	azure rediscache set [--name <name> --resource-group <resource-group> --max-memory-policy <max-memory-policy>]

For more information about this command, run the `azure rediscache set -h` command.

	C:\>azure rediscache set -h
	help:    Change settings of an existing Redis Cache
	help:
	help:    Usage: rediscache set [--name <name> --resource-group <resource-group> --max-memory-policy <max-memory-policy>]
	help:
	help:    Options:
	help:      -h, --help                                   output usage information
	help:      -v, --verbose                                use verbose output
	help:      -vv                                          more verbose with debug output
	help:      --json                                       use json output
	help:      -n, --name <name>                            Name of the Redis Cache.
	help:      -g, --resource-group <resource-group>        Name of the Resource Group
	help:      -m, --max-memory-policy <max-memory-policy>  Max Memory Policy of the Redis Cache. Valid values: [AllKeysLRU, AllKeysRandom, NoEviction, VolatileLRU, VolatileRandom, VolatileTTL]
	help:      -s, --subscription <subscription>            the subscription identifier
	help:
	help:    Current Mode: arm (Azure Resource Management)

## Renew the authentication key for an existing Redis Cache

To renew the authentication key for an existing Redis Cache, use the following command:

	azure rediscache renew-key [--name <name> --resource-group <resource-group> --key-type <key-type>]

Specify `Primary` or `Secondary` for `key-type`.

For more information about this command, run the `azure rediscache renew-key -h` command.

	C:\>azure rediscache renew-key -h
	help:    Renew the authentication key for an existing Redis Cache
	help:
	help:    Usage: rediscache renew-key [--name <name> --resource-group <resource-group> ]
	help:
	help:    Options:
	help:      -h, --help                             output usage information
	help:      -v, --verbose                          use verbose output
	help:      -vv                                    more verbose with debug output
	help:      --json                                 use json output
	help:      -n, --name <name>                      Name of the Redis Cache.
	help:      -g, --resource-group <resource-group>  Name of the Resource Group under which cache exists
	help:      -t, --key-type <key-type>              type of key to renew
	help:      -s, --subscription <subscription>      the subscription identifier
	help:
	help:    Current Mode: arm (Azure Resource Management)

## List Primary and Secondary keys of an existing Redis Cache

To list Primary and Secondary keys of an existing Redis Cache, use the following command:

	azure rediscache list-keys [--name <name> --resource-group <resource-group>]

For more information about this command, run the `azure rediscache list-keys -h` command.

	C:\>azure rediscache list-keys -h
	help:    Lists Primary and Secondary key of an existing Redis Cache
	help:
	help:    Usage: rediscache list-keys [--name <name> --resource-group <resource-group>]
	help:
	help:    Options:
	help:      -h, --help                             output usage information
	help:      -v, --verbose                          use verbose output
	help:      -vv                                    more verbose with debug output
	help:      --json                                 use json output
	help:      -n, --name <name>                      Name of the Redis Cache.
	help:      -g, --resource-group <resource-group>  Name of the Resource Group under which Cache exists
	help:      -s, --subscription <subscription>      the subscription identifier
	help:
	help:    Current Mode: arm (Azure Resource Management)