---
title: Publikování balíčku NuGet
description: Doporučení osvědčených postupů pro publikování knihoven .NET na NuGet.
ms.date: 10/02/2018
ms.openlocfilehash: 089c660bc51252c6295858b1462ae59bde968564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744553"
---
# <a name="publishing-a-nuget-package"></a>Publikování balíčku NuGet

Balíčky NuGet jsou publikovány a spotřebovávány z úložišť balíčků. Zatímco NuGet.org je nejznámější a nejpoužívanější úložiště, existuje mnoho míst k publikování balíčků NuGet:

* **[NuGet.org](https://www.nuget.org/)** je primární online úložiště pro balíčky NuGet. Všechny balíčky na NuGet.org jsou veřejně dostupné všem. Ve výchozím nastavení visual studio NuGet.org jako zdroj balíčku a pro mnoho vývojářů NuGet.org je pouze úložiště balíčků, které budou pracovat. NuGet.org je nejlepší místo pro publikování stabilních balíčků a předběžných verzí balíčků, na které chcete získat zpětnou vazbu komunity.

* **[MyGet](https://myget.org/)** je služba úložiště, která podporuje vlastní kanály balíčků pro open source projekty. Veřejný vlastní zdroj MyGet je ideálním místem pro publikování předběžných balíčků vytvořených vaší službou CI. MyGet také poskytuje soukromé kanály komerčně.

* **[Místní informační kanál](/nuget/hosting-packages/local-feeds)** umožňuje zacházet se složkou jako `*.nupkg` úložiště balíčků a zpřístupňuje soubory ve složce nuget. Místní zdroj je užitečné pro testování balíčku NuGet před publikováním na NuGet.org.

> [!NOTE]
> NuGet.org [neumožňuje odstranění balíčku](/nuget/policies/deleting-packages) po jeho odeslání. Balíček může být neuveden, takže není veřejně viditelný v `*.nupkg` ui, ale lze jej stále stáhnout při obnovení. nuget.org také neumožňuje duplicitní verze balíčků. Chcete-li opravit balíček NuGet s chybou, musíte zrušit seznam nesprávného balíčku, vzrůst číslo verze a publikovat novou verzi balíčku.

✔️ DO [publikovat stabilní balíčky a předběžné verze balíčků,](/nuget/create-packages/publish-a-package) které chcete, aby komunita zpětná vazba na NuGet.org.

✔️ ZVAŽTe publikování předběžných balíčků do informačního kanálu MyGet z průběžné integrace sestavení.

✔️ zvážit testování balíčků ve vývojovém prostředí pomocí místního kanálu nebo MyGet. Zkontrolujte, zda balíček funguje a pak publikovat do NuGet.org.

## <a name="nugetorg-security"></a>NuGet.org zabezpečení

Je důležité, aby chybní herci nemohli získat přístup k vašemu účtu NuGet a nahrát škodlivou verzi knihovny. NuGet.org nabízí dvoufaktorové ověřování a e-mailová oznámení při publikování balíčku. Po přihlášení k NuGet.org na stránce **Nastavení účtu** povolte tyto funkce.

![alternativní text](./media/publish-nuget-package/nuget-2fa.png "Zabezpečení účtu NuGet")

✔️ do použít účet Microsoft pro přihlášení k NuGet.

✔️ DO povolit dvoufaktorové ověřování pro přístup k NuGet.

✔️ do povolit e-mailové oznámení při publikování balíčku.

>[!div class="step-by-step"]
>[Předchozí](sourcelink.md)
>[další](versioning.md)
