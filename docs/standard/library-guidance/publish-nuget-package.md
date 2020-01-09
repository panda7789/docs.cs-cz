---
title: Publikování balíčku NuGet
description: Doporučení osvědčených postupů pro publikování knihoven .NET do NuGet.
ms.date: 10/02/2018
ms.openlocfilehash: e567fe3f7e00bf322cdd50786e50128961107469
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706462"
---
# <a name="publishing-a-nuget-package"></a>Publikování balíčku NuGet

Balíčky NuGet se zveřejňují a spotřebovávají z úložišť balíčků. I když je NuGet.org nejčastěji známé a používané úložiště, je k dispozici mnoho míst pro publikování balíčků NuGet:

* **[NuGet.org](https://www.nuget.org/)** je primární online úložiště pro balíčky NuGet. Všechny balíčky v NuGet.org jsou veřejně dostupné všem uživatelům. Ve výchozím nastavení sada Visual Studio NuGet.org jako zdroj balíčku a pro mnoho vývojářů NuGet.org je jediným úložištěm balíčků, se kterým budou pracovat. NuGet.org je to nejlepší místo pro publikování stabilních balíčků a předběžných vydaných balíčků, na které chcete komunitu poskytovat názory.

* **[MyGet](https://myget.org/)** je služba úložiště, která podporuje vlastní kanály balíčků pro open source projekty. Vlastní informační kanál MyGet je ideálním místem pro publikování předběžných verzí balíčků vytvořených službou CI. MyGet také poskytuje soukromé informační kanály komerčně.

* **[Místní kanál](/nuget/hosting-packages/local-feeds)** umožňuje považovat složku jako úložiště balíčků a zpřístupňuje soubory `*.nupkg` ve složce přístupné pomocí NuGet. Místní kanál je vhodný pro otestování balíčku NuGet před jeho publikováním na NuGet.org.

> [!NOTE]
> NuGet.org [neumožňuje odstranění balíčku](/nuget/policies/deleting-packages) po jeho nahrání. Balíček může být nezobrazený, aby nebyl veřejně viditelný v uživatelském rozhraní, ale `*.nupkg` se pořád dá stáhnout při obnovení. Nuget.org také nepovoluje duplicitní verze balíčků. Chcete-li opravit balíček NuGet s chybou, je třeba zrušit seznam nesprávného balíčku, zvýšit číslo verze a publikovat novou verzi balíčku.

**✔️** [publikovat stabilní balíčky a předběžné verze balíčků](/nuget/create-packages/publish-a-package) , ve kterých chcete, aby se komunitní názory na NuGet.org.

**✔️ zvažte** publikování předběžných verzí balíčků do MyGet kanálu ze sestavení průběžné integrace.

**✔️ zvažte** testování balíčků ve vývojovém prostředí pomocí místního informačního kanálu nebo MyGet. Zkontrolujte, jestli balíček funguje, a pak ho publikujte na NuGet.org.

## <a name="nugetorg-security"></a>Zabezpečení NuGet.org

Je důležité, aby chybné objekty actor měly přístup k vašemu účtu NuGet a nahráli škodlivou verzi vaší knihovny. NuGet.org nabízí dvojúrovňové ověřování a e-mailová oznámení při publikování balíčku. Tyto funkce povolte po přihlášení k NuGet.org na stránce **Nastavení účtu** .

![alternativní text](./media/publish-nuget-package/nuget-2fa.png "Zabezpečení účtu NuGet")

k přihlášení do NuGet se **✔️** použít účet Microsoft.

**✔️** povolit dvojúrovňové ověřování pro přístup k nugetu.

Při publikování balíčku **✔️** povolit e-mailová oznámení.

>[!div class="step-by-step"]
>[Předchozí](sourcelink.md)
>[Další](versioning.md)
