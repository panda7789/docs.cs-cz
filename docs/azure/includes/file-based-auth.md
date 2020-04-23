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
<span data-ttu-id="f358c-101">Vytvořte textový `azureauth.json`soubor s názvem .</span><span class="sxs-lookup"><span data-stu-id="f358c-101">Create a text file named `azureauth.json`.</span></span> <span data-ttu-id="f358c-102">Vložte výstup JSON z při vytvoření instančního objektu.</span><span class="sxs-lookup"><span data-stu-id="f358c-102">Paste the JSON output from when you created the service principal.</span></span>

<span data-ttu-id="f358c-103">Uložte tento soubor na bezpečné místo ve vašem systému, kde z něho bude moct číst váš kód.</span><span class="sxs-lookup"><span data-stu-id="f358c-103">Save this file in a secure location on your system where your code can read it.</span></span> <span data-ttu-id="f358c-104">Pomocí prostředí PowerShell nastavte `AZURE_AUTH_LOCATION` proměnnou prostředí pojmenovanou s úplnou cestou k souboru, například:</span><span class="sxs-lookup"><span data-stu-id="f358c-104">Use PowerShell to set an environment variable named `AZURE_AUTH_LOCATION` with the full path to the file, for example:</span></span>

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.json", "User")
```
