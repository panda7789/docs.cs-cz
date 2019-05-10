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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23a05279615a589bca7bb61507caf8dcc3630020
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648711"
---
# <a name="importing-a-type-library-as-an-assembly"></a>Import knihovny typů ve formě sestavení
Definice typů modelu COM jsou obvykle umístěny v knihovně typů. Naproti tomu kompatibilní se Specifikací CLS kompilátory vytvářejí metadat typu v sestavení. Dva zdroje informací o typu se značně liší. Toto téma popisuje postupy pro generování metadat z knihovny typů. Výsledné sestavení se nazývá definiční sestavení a, které obsahuje informace o typu umožňuje používat typy modelu COM aplikacemi rozhraní .NET Framework.  
  
 Existují dva způsoby, jak zpřístupnit tento typ informace pro vaši aplikaci:  
  
- Použití pouze pro návrh definiční sestavení: Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], můžete dát pokyn kompilátoru k vložení informací o typu ze sestavení vzájemné spolupráce do spustitelného souboru. Kompilátor vloží jenom informace o typu, který vaše aplikace používá. Není nutné k nasazení sestavení vzájemné spolupráce s vaší aplikací. Toto je doporučený postup.  
  
- Nasazení sestavení vzájemné spolupráce: Můžete vytvořit standardní odkaz na sestavení vzájemné spolupráce. V takovém případě musí být nasazeny sestavení zprostředkovatele komunikace s vaší aplikací. Pokud nepoužijete tento postup a nepoužíváte Soukromá komponenta modelu COM, vždycky odkazujte na sestavení primární spolupráce (PIA) publikoval Autor komponenty modelu COM, které chcete začlenit ve spravovaném kódu. Další informace o vytváření a používání sestavení primární spolupráce naleznete v tématu [Primary Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).  
  
 Pokud používáte pouze pro návrh sestavení vzájemné spolupráce, můžete vložit informací o typu ze sestavení primární spolupráce publikoval Autor komponenty modelu COM. Ale není potřeba nasazovat primární sestavení zprostředkovatele komunikace s vaší aplikací.  
  
 Pomocí návrhu pouze v době sestavení vzájemné spolupráce snižuje velikost vaší aplikace, protože většina aplikací se nepoužívá všechny funkce verze komponenty modelu COM. Kompilátoru je velmi efektivní při vloží informace o typu; Pokud vaše aplikace využívá jenom některé z metod na rozhraní modelu COM, nevloží kompilátor nepoužité metody. Když aplikaci, která obsahuje vložené informace o typu komunikuje s jiná taková aplikace nebo pracuje s aplikací, které používá primární sestavení zprostředkovatele komunikace, běžné použití modulu runtime jazyka zadejte ekvivalence pravidla za účelem zjištění, zda dva typy stejný název představují stejného modelu COM typu. Nemusíte vědět, tato pravidla používat objekty COM. Nicméně, pokud vás zajímá v pravidlech, naleznete v tématu [rovnocennosti typů a vestavěné typy spolupráce](../../../docs/framework/interop/type-equivalence-and-embedded-interop-types.md).  
  
## <a name="generating-metadata"></a>Generování metadat  
 Knihovny typů modelu COM může být samostatné soubory, které mají s příponou .tlb, jako je například Loanlib.tlb. Některé knihovny typů jsou vložené v oddílu prostředků ze souboru .dll nebo .exe. Další zdroje informací o typu knihovny jsou soubory, .olb a .ocx.  
  
 Po vyhledání knihovnu typů, která obsahuje implementace v cílovém typu modelu COM, máte následující možnosti pro generování sestavení vzájemné spolupráce obsahující typ metadat:  
  
- Visual Studio  
  
     Visual Studio automaticky převede typy modelu COM v knihovně typů na metadata do sestavení. Pokyny najdete v tématu [jak: Přidání odkazů do knihoven typů](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md).  
  
- [Importér knihovny typů (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
  
     Type Library Importer nabízí možnosti příkazového řádku, chcete-li upravit metadata ve výsledném souboru spolupráce, importuje typy z existující knihovnu typů a vygeneruje definiční sestavení a oboru názvů. Pokyny najdete v tématu [jak: Generování sestavení vzájemné spolupráce z knihoven typů](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).  
  
- <xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=nameWithType> Třída  
  
     Tato třída poskytuje metody pro převod třídy typu coclass a rozhraní v knihovně typů na metadata v rámci sestavení. Vytvoří stejný výstup metadat jako Tlbimp.exe. Ale na rozdíl od Tlbimp.exe <xref:System.Runtime.InteropServices.TypeLibConverter> třídy lze převést knihovnu typů v paměti k metadatům.  
  
- Vlastní obálky  
  
     Pokud knihovna typů je nedostupná nebo není správný, jednou z možností je vytvoření duplicitní definice třídy nebo rozhraní ve spravovaném zdrojovém kódu. Potom kompilaci zdrojového kódu s kompilátorem, zaměřuje na modul runtime k vytvoření metadat sestavení.  
  
     Chcete-li ručně definovat typy modelu COM, musí mít přístup k následujícím položkám:  
  
    - Přesné popis třídy typu coclass a rozhraní definuje.  
  
    - Kompilátor, jako C# kompilátoru, která mohou generovat odpovídající definice tříd rozhraní .NET Framework.  
  
    - Znalost pravidla sestavení knihovny převodu typu.  
  
     Psaní vlastních obálky je pokročilé techniky. Další informace o tom, jak generovat vlastní obálku najdete v tématu [přizpůsobení standardních obálek](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100)).  
  
 Další informace o importu vzájemné spolupráce COM, naleznete v tématu [sestavení souhrn převodu knihovny typů na](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- [Vystavení komponent COM pro rozhraní .NET Framework](../../../docs/framework/interop/exposing-com-components.md)
- [Souhrn převodu sestavení knihovny typů na](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Tlbimp.exe (importér knihovny typů)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)
- [Přizpůsobení standardních obálek](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))
- [Používání typů modelu COM ve spravovaném kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Kompilace projektu interoperability](../../../docs/framework/interop/compiling-an-interop-project.md)
- [Nasazení aplikace spolupráce](../../../docs/framework/interop/deploying-an-interop-application.md)
- [Postupy: Přidání odkazů do knihoven typů](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md)
- [Postupy: Generování sestavení vzájemné spolupráce z knihoven typů](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md)
