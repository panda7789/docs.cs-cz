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
ms.openlocfilehash: 89479ca4a41f761d4aacaf6d8d962bfba62be811
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393413"
---
# <a name="importing-a-type-library-as-an-assembly"></a>Import knihovny typů ve formě sestavení
Definice typů COM se obvykle nacházejí v knihovny typů. Naproti tomu kompatibilní se specifikací CLS kompilátory vytvořit typ metadat v sestavení. Dva zdroje informací o typu se výrazně lišit. Toto téma popisuje techniky pro generování metadat z knihovny typů. Výsledné sestavení je volána sestavení vzájemné spolupráce a informací o typu, který obsahuje umožňuje aplikacím používat typy modelu COM rozhraní .NET Framework.  
  
 Existují dva způsoby, jak zpřístupnit tento typ informace pro aplikace:  
  
-   Použití pouze pro návrh sestavení vzájemné spolupráce: od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], můžete určit, aby kompilátoru pro vložení informací o typu ze sestavení vzájemné spolupráce do spustitelného souboru. Kompilátor vloží pouze typ informace, které vaše aplikace používá. Nemusíte nasazovat sestavení vzájemné spolupráce s vaší aplikací. Toto je doporučený postup.  
  
-   Nasazení sestavení vzájemné spolupráce: můžete vytvořit standardní odkaz na sestavení vzájemné spolupráce. V takovém případě musí být nasazený sestavení vzájemné spolupráce s vaší aplikací. Pokud nepoužijete tento postup a nepoužíváte privátní komponenty modelu COM, vždy referenční sestavení primární spolupráce (PIA), které zveřejnil Autor komponenty modelu COM, které chcete mít ve spravovaném kódu. Další informace o vytváření a používání primárních sestavení vzájemné spolupráce najdete v tématu [primární zprostředkovatel komunikace s objekty sestavení](https://msdn.microsoft.com/library/b977a8be-59a0-40a0-a806-b11ffba5c080(v=vs.100)).  
  
 Pokud používáte pouze pro návrh sestavení vzájemné spolupráce, můžete vložit informací o typu ze primárních sestavení vzájemné spolupráce publikováno autora komponenty modelu COM. Však nemáte nasazení primárních sestavení vzájemné spolupráce s vaší aplikací.  
  
 Pomocí sestavení vzájemné spolupráce pouze pro návrh snižuje velikost vaší aplikace, protože většina aplikací nepoužívejte všechny funkce komponenty modelu COM. Kompilátor je velmi efektivní, když se vloží informace o typu; Pokud vaše aplikace využívá jenom některé z metod na rozhraní modelu COM, nevloží kompilátor nepoužívané metody. Pokud aplikaci, která má vložené informace o typu komunikuje s jiná takové aplikace, nebo komunikuje se službou aplikace, která používá primární spolupracující sestavení, zadejte běžná použití modulu runtime jazyka pravidla ekvivalenční k určení, zda dva typy s stejný název představují stejného typu COM. Nemusíte vědět těchto pravidel můžete použít objekty modelu COM. Ale pokud vás zajímá v pravidlech, najdete v části [ekvivalence typů a vložené typy zprostředkovatel komunikace s objekty](../../../docs/framework/interop/type-equivalence-and-embedded-interop-types.md).  
  
## <a name="generating-metadata"></a>Generování metadat  
 Knihovny typů COM může být samostatné soubory, které mají příponu .tlb například Loanlib.tlb. Některé knihovny typů jsou vloženy do části prostředků souboru .dll nebo .exe. Další zdroje informací o typu knihovny se soubory .olb a .ocx.  
  
 Po vyhledání knihovny typů, které obsahuje implementaci cílových typu modelu COM, máte následující možnosti pro generování sestavení vzájemné spolupráce obsahující metadata typu:  
  
-   Visual Studio  
  
     Visual Studio automaticky převede typy modelu COM v knihovně typů metadat v sestavení. Pokyny najdete v tématu [postupy: Přidání odkazů na knihovny typů](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md) a [návod: vložení informací o typu ze sestavení sady Microsoft Office](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100)).  
  
-   [Knihovna typů – Importér (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
  
     Knihovna typů – Importér poskytuje možnosti příkazového řádku upravit metadata ve výsledném souboru spolupráce, naimportuje typy z existující typ knihovny a generuje spolupráce sestavení a obor názvů. Pokyny najdete v tématu [postupy: generování sestavení zprostředkovatel komunikace s objekty z knihoven typů](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).  
  
-   <xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=nameWithType> – Třída  
  
     Tato třída poskytuje metody pro třídy typu coclass a rozhraní v knihovně typ převést metadata v rámci sestavení. Vyvolá stejný výstup metadat jako Tlbimp.exe. Ale na rozdíl od Tlbimp.exe <xref:System.Runtime.InteropServices.TypeLibConverter> třídy můžete převést knihovny typů v paměti metadat.  
  
-   Vlastní obálky  
  
     Knihovny typů je k dispozici nebo není správný, jednou z možností je vytvořit duplicitní definice třídy nebo rozhraní ve spravovaných zdrojovém kódu. Potom kompilaci zdrojového kódu s kompilátorem zacílený runtime k vytvoření metadat v sestavení.  
  
     Chcete-li ručně definovat typy modelu COM, musíte mít přístup k následujícím položkám:  
  
    -   Přesné popis třídy typu coclass a rozhraní definovaný.  
  
    -   Kompilátor, jako je například kompilátor C#, který může vytvořit příslušné definice tříd rozhraní .NET Framework.  
  
    -   Znalost pravidel převodu sestavení knihovny typů.  
  
     Psaní vlastních obálku je pokročilé techniky. Další informace o tom, jak vygenerovat vlastní obálku najdete v tématu [přizpůsobení standardní obálky](https://msdn.microsoft.com/library/c40d089b-6a3c-41b5-a20d-d760c215e49d(v=vs.100)).  
  
 Další informace o importu zprostředkovatele komunikace s objekty COM, najdete v části [knihovny typů pro souhrn konverze sestavení](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.TypeLibConverter>  
 [Vystavení komponent COM pro rozhraní .NET Framework](../../../docs/framework/interop/exposing-com-components.md)  
 [Knihovny typů pro souhrn konverze sestavení](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100))  
 [Tlbimp.exe (importér knihovny typů)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
 [Přizpůsobení standardních obálek](https://msdn.microsoft.com/library/c40d089b-6a3c-41b5-a20d-d760c215e49d(v=vs.100))  
 [Použití typy modelu COM ve spravovaném kódu](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))  
 [Kompilace projektu interoperability](../../../docs/framework/interop/compiling-an-interop-project.md)  
 [Nasazení aplikace spolupráce](../../../docs/framework/interop/deploying-an-interop-application.md)  
 [Postupy: Přidávání odkazů do knihoven typů](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md)  
 [Postupy: Generování sestavení vzájemné spolupráce z knihoven typů](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md)  
 [Návod: Vložení informací o typu ze sestavení Microsoft Office](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))
