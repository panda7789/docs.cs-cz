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
Vytvořte textový `azureauth.json`soubor s názvem . Vložte výstup JSON z při vytvoření instančního objektu.

Uložte tento soubor na bezpečné místo ve vašem systému, kde z něho bude moct číst váš kód. Pomocí prostředí PowerShell nastavte `AZURE_AUTH_LOCATION` proměnnou prostředí pojmenovanou s úplnou cestou k souboru, například:

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.json", "User")
```
