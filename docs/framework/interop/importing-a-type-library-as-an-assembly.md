---
title: Import knihovny typů ve formě sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- type metadata
- custom wrappers
- metadata
- exposing COM components to .NET Framework
- Type Library Importer
- interoperation with unmanaged code, importing type library
- interoperation with unmanaged code, exposing COM components
- type libraries
- TypeLibConverter class, importing type library as assembly
- COM interop, importing type library
- COM interop, exposing COM components
ms.assetid: d1898229-cd40-426e-a275-f3eb65fbc79f
ms.openlocfilehash: e1a21175bcabc72b86a328d4f73ecec37140c304
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107588"
---
# <a name="importing-a-type-library-as-an-assembly"></a>Import knihovny typů ve formě sestavení

Definice typu modelu COM jsou obvykle umístěny v knihovně typů. V kontrastu kompilátory odpovídající specifikaci CLS vytváří metadata typu v sestavení. Dva zdroje informací o typu jsou poměrně odlišné. Toto téma popisuje techniky pro generování metadat z knihovny typů. Výsledné sestavení se nazývá definiční sestavení a informace o typu, které obsahuje, umožňuje .NET Framework aplikacím používat typy COM.

Existují dva způsoby, jak tyto informace o typu zpřístupnit vaší aplikaci:

- Použití spolupracujících sestavení s pouze návrhem: počínaje .NET Framework 4 můžete instruovat kompilátor pro vložení informací o typu ze sestavení interop do spustitelného souboru. Kompilátor vloží pouze informace o typu, které vaše aplikace používá. Sestavení vzájemné spolupráce není nutné nasazovat do aplikace. Toto je doporučený postup.

- Nasazení definičních sestavení: můžete vytvořit standardní odkaz na definiční sestavení. V takovém případě musí být definiční sestavení nasazeno s vaší aplikací. Pokud použijete tento postup a nepoužíváte privátní komponentu modelu COM, vždy se na primární definiční sestavení (PIA) publikované autorem komponenty modelu COM, kterou máte v úmyslu začlenit do spravovaného kódu, vždy odkázat. Další informace o vytváření a používání primárních sestavení vzájemné spolupráce naleznete v tématu [primární spolupracující sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).

Pokud používáte interoperabilní sestavení pouze pro návrh, můžete vložit informace o typu z primárního definičního sestavení publikovaného autorem komponenty modelu COM. Není však nutné nasazovat primární definiční sestavení s vaší aplikací.

Použití spolupracujících sestavení pouze při návrhu snižuje velikost vaší aplikace, protože většina aplikací nepoužívá všechny funkce komponenty modelu COM. Kompilátor je velmi efektivní při vložení informací o typu; Pokud vaše aplikace používá pouze některé metody rozhraní COM, kompilátor nevloží nepoužívané metody. Když aplikace, která obsahuje informace o vloženém typu, spolupracuje s jinou takovou aplikací nebo komunikuje s aplikací, která používá primární definiční sestavení, modul CLR používá pravidla rovnocennosti typů k určení, zda dva typy s stejný název představuje stejný typ COM. Tato pravidla nemusíte znát, chcete-li používat objekty COM. Nicméně pokud vás zajímá pravidla, přečtěte si téma [typ ekvivalence a vložené typy spolupráce](type-equivalence-and-embedded-interop-types.md).

## <a name="generating-metadata"></a>Generování metadat

Knihovny typů modelu COM můžou být samostatné soubory, které mají příponu. tlb, například LOANLib. tlb. Některé knihovny typů jsou vloženy do oddílu prostředků souboru. dll nebo. exe. Další zdroje informací o knihovně typů jsou soubory. olb a. ocx.

Po nalezení knihovny typů, která obsahuje implementaci cílového typu modelu COM, máte následující možnosti pro generování sestavení vzájemné spolupráce obsahující metadata typu:

- Visual Studio

  Visual Studio automaticky převede typy modelu COM v knihovně typů na metadata v sestavení. Pokyny najdete v tématu [Postupy: Přidání odkazů do knihoven typů](how-to-add-references-to-type-libraries.md).

- [Importér knihovny typů (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md)

  Importér knihovny typů poskytuje možnosti příkazového řádku pro úpravu metadat ve výsledném definičním souboru, naimportuje typy z existující knihovny typů a vygeneruje definiční sestavení a obor názvů. Pokyny naleznete v tématu [How to: Generate spolupracující sestavení z knihoven typů](how-to-generate-interop-assemblies-from-type-libraries.md).

- <xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=nameWithType> – třída

  Tato třída poskytuje metody pro převod tříd typu coclass a rozhraní v knihovně typů na metadata v rámci sestavení. Vytváří stejný výstup metadat jako Tlbimp. exe. Nicméně na rozdíl od nástroje Tlbimp. exe může třída <xref:System.Runtime.InteropServices.TypeLibConverter> převést knihovnu typů v paměti na metadata.

- Vlastní obálky

  Pokud není knihovna typů k dispozici nebo je nesprávná, jedna z možností je vytvořit duplicitní definici třídy nebo rozhraní ve spravovaném zdrojovém kódu. Poté zkompilujete zdrojový kód s kompilátorem, který cílí na modul runtime, aby vytvořil metadata v sestavení.

  Chcete-li definovat typy COM ručně, musíte mít přístup k následujícím položkám:

  - Přesné popisy tříd a rozhraní, které jsou definovány.

  - Kompilátor, jako je C# například kompilátor, který může generovat příslušné definice .NET Framework třídy.

  - Znalosti typu pravidla převodu knihovny na sestavení.

  Vytvoření vlastní obálky je pokročilá technika. Další informace o tom, jak vygenerovat vlastní obálku, najdete v tématu [přizpůsobení standardních obálek](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100)).

 Další informace o procesu importu zprostředkovatele komunikace s objekty COM naleznete v tématu [Souhrn převodu knihovny typů na sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)).

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- [Vystavení komponent COM pro rozhraní .NET Framework](exposing-com-components.md)
- [Souhrn převodu knihovny typů na sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Tlbimp.exe (importér knihovny typů)](../tools/tlbimp-exe-type-library-importer.md)
- [Přizpůsobení standardních obálek](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))
- [Použití typů modelu COM ve spravovaném kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Kompilace projektu interoperability](compiling-an-interop-project.md)
- [Nasazení aplikace spolupráce](deploying-an-interop-application.md)
- [Postupy: Přidávání odkazů do knihoven typů](how-to-add-references-to-type-libraries.md)
- [Postupy: Generování sestavení vzájemné spolupráce z knihoven typů](how-to-generate-interop-assemblies-from-type-libraries.md)
