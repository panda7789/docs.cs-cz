---
ms.openlocfilehash: 6cdd410cc818c2c0a993a364e550f5f92ed6a821
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981823"
---
### <a name="resgen-refuses-to-load-content-from-the-web"></a><span data-ttu-id="aefc3-101">Resgen odmítá k načtení obsahu z webu</span><span class="sxs-lookup"><span data-stu-id="aefc3-101">Resgen refuses to load content from the web</span></span>

|   |   |
|---|---|
|<span data-ttu-id="aefc3-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="aefc3-102">Details</span></span>|<span data-ttu-id="aefc3-103">binární formátovaný vstup může obsahovat soubory .resx.</span><span class="sxs-lookup"><span data-stu-id="aefc3-103">.resx files may contain binary formatted input.</span></span> <span data-ttu-id="aefc3-104">Pokud se pokusíte použít aplikaci resgen se načíst soubor, který byl stažen z nedůvěryhodného umístění, se nepovedlo se načíst vstupní ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="aefc3-104">If you attempt to use resgen to load a file that was downloaded from an untrusted location, it will fail to load the input by default.</span></span>|
|<span data-ttu-id="aefc3-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="aefc3-105">Suggestion</span></span>|<span data-ttu-id="aefc3-106">Resgen, kteří vyžadují načítání binární formátovaný vstup z nedůvěryhodného umístění můžete odebrat značku webu ze vstupního souboru nebo použít datového toku zvuku nabízí výslovného nesouhlasu s. Přidejte následující nastavení registru použít počítač široký odhlásit datového toku zvuku nabízí: [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework\SDK] &quot;AllowProcessOfUntrustedResourceFiles&quot;=&quot;true&quot;</span><span class="sxs-lookup"><span data-stu-id="aefc3-106">Resgen users who require loading binary formatted input from untrusted locations can either remove the mark of the web from the input file or apply the opt-out quirk.Add the following registry setting to apply the machine wide opt-out quirk: [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework\SDK] &quot;AllowProcessOfUntrustedResourceFiles&quot;=&quot;true&quot;</span></span>|
|<span data-ttu-id="aefc3-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="aefc3-107">Scope</span></span>|<span data-ttu-id="aefc3-108">Edge</span><span class="sxs-lookup"><span data-stu-id="aefc3-108">Edge</span></span>|
|<span data-ttu-id="aefc3-109">Version</span><span class="sxs-lookup"><span data-stu-id="aefc3-109">Version</span></span>|<span data-ttu-id="aefc3-110">4.7.2</span><span class="sxs-lookup"><span data-stu-id="aefc3-110">4.7.2</span></span>|
|<span data-ttu-id="aefc3-111">Type</span><span class="sxs-lookup"><span data-stu-id="aefc3-111">Type</span></span>|<span data-ttu-id="aefc3-112">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="aefc3-112">Retargeting</span></span>|
