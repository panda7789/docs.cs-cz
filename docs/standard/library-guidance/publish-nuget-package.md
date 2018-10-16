---
title: Publikování balíčku NuGet
description: Doporučení osvědčených postupů pro publikování knihovny .NET NuGet
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 0602712311411ef3d59825bec8c5e550bc8d8265
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2018
ms.locfileid: "49337657"
---
# <a name="publishing-a-nuget-package"></a>Publikování balíčku NuGet

Balíčky NuGet se publikovat a použít z úložišť balíčků. I když NuGet.org nejčastěji známé a využité úložiště, publikovat balíčky NuGet mnoho místech:

* **[NuGet.org](https://www.nuget.org/)**  slouží jako primární online úložiště balíčků NuGet. Všech balíčků na NuGet.org jsou veřejně dostupné pro všechny uživatele. Ve výchozím nastavení Visual Studio má NuGet.org jako zdroj balíčků a řada vývojářů NuGet.org je pouze úložiště balíčků, kterou budete pracovat. NuGet.org je nejlepším místem, kde můžete publikovat stabilní balíčky a balíčky v předběžné verzi, které chcete zpětná vazba komunity na.

* **[MyGet](https://myget.org/)**  úložiště služba podporuje [zdarma vlastní balíček informační kanály pro open source projektů](https://www.myget.org/opensource). MyGet veřejné vlastního kanálu je ideálním místem pro publikovat balíčky v předběžné verzi vytvořené služby CI. MyGet také poskytuje privátní kanály komerčně.

* A **[místní informační kanál](/nuget/hosting-packages/local-feeds)** umožňuje přistupovat ke všem složku jako úložiště balíčků a zpřístupňuje `*.nupkg` soubory ve složce přístupný balíčkem NuGet. Místní informační kanál je užitečné pro testování před publikováním na NuGet.org balíčku NuGet.

> [!NOTE]
> NuGet.org [neumožňuje balíček odstranit](/nuget/policies/deleting-packages) po nahrání. Balíček může neuvedené tak, že není veřejně viditelné v uživatelském rozhraní ale `*.nupkg` stále je možné stáhnout na obnovení. Navíc nuget.org nepovoluje duplicitní balíčku verze. Chcete-li opravit balíček NuGet s chybou budete muset vyjmutí ze seznamu nesprávné balíčku, zvýší číslo verze a publikujte novou verzi balíčku.

**PROVEĎTE ✔️** [publikovat stabilní balíčky a balíčky v předběžné verzi](/nuget/create-packages/publish-a-package) chcete zpětná vazba komunity na NuGet.org.

**✔️ ZVAŽTE** publikování balíčky v předběžné verzi MyGet informačního kanálu ze sestavení kontinuální integrace.

**✔️ ZVAŽTE** testování balíčků ve vašem vývojovém prostředí pomocí místního kanálu či MyGet. Zkontrolujte balíček funguje potom ji publikovat na NuGet.org.

## <a name="nugetorg-security"></a>Zabezpečení NuGet.org

Je důležité, že nelze přístup k vašemu účtu NuGet a odeslat škodlivý verzi knihovny. NuGet.org nabízí dvojúrovňového ověřování a e-mailové oznámení, když se publikuje balíček. Tyto funkce povolit po přihlášení na NuGet.org na **nastavení účtu** stránky.

![alternativní text](./media/publish-nuget-package/nuget-2fa.png "zabezpečení účtu NuGet")

**PROVEĎTE ✔️** použít účet Microsoft pro přihlášení k NuGet.

**PROVEĎTE ✔️** povolení dvoufaktorového ověřování pro přístup k NuGet.

**PROVEĎTE ✔️** povolit e-mailové oznámení, když se publikuje balíček.

>[!div class="step-by-step"]
[Předchozí](./sourcelink.md)
[další](./versioning.md)
