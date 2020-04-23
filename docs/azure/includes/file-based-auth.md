---
ms.service: multiple
ms.date: 9/20/2018
ms.topic: include
ms.openlocfilehash: bfa7bcefff45bc325d7bba3aa2b9b3a8f0d439fa
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071932"
---
Vytvořte textový soubor s názvem `azureauth.json`. Při vytváření instančního objektu vložte výstup JSON.

Uložte tento soubor na bezpečné místo ve vašem systému, kde z něho bude moct číst váš kód. Pomocí PowerShellu nastavte proměnnou prostředí s názvem `AZURE_AUTH_LOCATION` úplnou cestou k souboru, třeba:

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.json", "User")
```
