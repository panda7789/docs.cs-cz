---
ms.service: multiple
ms.date: 9/20/2018
ms.topic: include
ms.openlocfilehash: c3746ff92838ac97d8158a0daf0b1a1de07ae024
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071981"
---
Vaše aplikace .NET potřebuje oprávnění ke čtení a vytváření prostředků ve vašem předplatném Azure, aby bylo možné používat knihovny Azure Management pro .NET. Vytvořte instanční objekt a nakonfigurujte aplikaci tak, aby běžela s jeho přihlašovacími údaji, aby tento přístup udělila. Instanční objekty představují způsob, jak vytvořit neinteraktivní účet přidružený k vaší identitě, kterému udělíte pouze oprávnění potřebná k fungování vaší aplikace.

Nejprve se přihlaste do [služby Azure Cloud Shell](https://shell.azure.com/bash). Ověřte, zda aktuálně používáte předplatné, ve kterém chcete vytvořit instanční objekt.

```azurecli-interactive
az account show
```

Zobrazí se informace o vašem předplatném.

```json
{
  "environmentName": "AzureCloud",
  "id": "15dbcfa8-4b93-4c9a-881c-6189d39f04d4",
  "isDefault": true,
  "name": "my-subscription",
  "state": "Enabled",
  "tenantId": "43413cc1-5886-4711-9804-8cfea3d1c3ee",
  "user": {
    "cloudShellID": true,
    "name": "jane@contoso.com",
    "type": "user"
  }
}
```

Pokud nejste přihlášeni ke správnému předplatnému, vyberte `az account set -s <name or ID of subscription>`správné předplatné zadáním .

Vytvořte instanční objekt s následujícím příkazem:

```azurecli-interactive
az ad sp create-for-rbac --sdk-auth
```

Informace o instančním objektu se zobrazí jako JSON.

```json
{
  "clientId": "b52dd125-9272-4b21-9862-0be667bdf6dc",
  "clientSecret": "ebc6e170-72b2-4b6f-9de2-99410964d2d0",
  "subscriptionId": "ffa52f27-be12-4cad-b1ea-c2c241b6cceb",
  "tenantId": "72f988bf-86f1-41af-91ab-2d7cd011db47",
  "activeDirectoryEndpointUrl": "https://login.microsoftonline.com",
  "resourceManagerEndpointUrl": "https://management.azure.com/",
  "activeDirectoryGraphResourceId": "https://graph.windows.net/",
  "sqlManagementEndpointUrl": "https://management.core.windows.net:8443/",
  "galleryEndpointUrl": "https://gallery.azure.com/",
  "managementEndpointUrl": "https://management.core.windows.net/"
}
```

Zkopírujte a vložte výstup JSON do textového editoru pro pozdější použití.
