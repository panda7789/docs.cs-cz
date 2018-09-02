---
title: Představení zprostředkovatele komunikace s objekty COM (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
ms.openlocfilehash: ecd514231c36cf3b65b1f0dd05f26d05f3c9c88d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389741"
---
# <a name="introduction-to-com-interop-visual-basic"></a>Představení zprostředkovatele komunikace s objekty COM (Visual Basic)
Modelu COM (Component Object) umožňuje objektu jeho funkcionalitu, ostatních komponentách a k hostování aplikací. Zatímco objekty modelu COM byly nezbytné k programování po mnoho let Windows, aplikací navržených pro modul common language runtime (CLR) nabízí celou řadu výhod.  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikace bude nakonec nahradí vyvinuté pomocí modelu COM. Dokud to neuděláte bude pravděpodobně nutné použít nebo vytvořit objekty modelu COM s použitím sady Visual Studio. Vzájemná funkční spolupráce s modelu COM, nebo *komunikace s objekty COM*, vám umožní použít při přechodu do existujících objektů COM [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] svým vlastním tempem.  
  
 S použitím [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] vytváření komponent modelu COM, můžete použít spolupráci s COM bez registrace. To vám umožňuje řídit, kterou verzi knihovny DLL povolíte více než jedna verze je nainstalovaná na počítači a umožňuje koncovým uživatelům pomocí příkazu XCOPY nebo FTP aplikaci do příslušného adresáře v počítači, kde lze spustit. Další informace najdete v tématu [spolupráci s COM bez registrace](https://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd).  
  
## <a name="managed-code-and-data"></a>Spravovaný kód a Data  
 Kód vyvinutý pro [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] se označuje jako *spravovaného kódu*a obsahuje metadata, která je používaná platformou CLR. Data používaná [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikacím se říká *dat spravovaných* vzhledem k tomu, že modul runtime spravuje úlohy související s daty, jako je kontrola typu přidělování a uvolní paměť a provádění. Ve výchozím nastavení Visual Basic .NET používá spravovaný kód a data, ale přístup k nespravovanému kódu a data objektů COM pomocí sestavení vzájemné spolupráce (popsaný níže na této stránce).  
  
## <a name="assemblies"></a>Sestavení  
 Sestavení je primární stavebním blokem [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikace. Jde o kolekci funkcí, které jsou připravené, čísly verzí a nasazených jako jedna implementace jednotku obsahující jeden nebo více souborů. Každé sestavení obsahuje manifest sestavení.  
  
## <a name="type-libraries-and-assembly-manifests"></a>Manifesty sestavení a knihoven typů  
 Knihovny typů popisují vlastnosti objektů modelu COM, jako jsou názvy členů a datové typy. Manifesty sestavení provádí stejnou funkci pro [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikací. Patří mezi ně následující informace:  
  
-   Identitu sestavení, verzi, jazykovou verzi a digitální podpis.  
  
-   Soubory, které tvoří sestavení implementace.  
  
-   Typy a prostředky, které tvoří sestavení. To zahrnuje ty, které jsou exportovány z něj.  
  
-   Kompilace závislosti na ostatních sestaveních.  
  
-   Oprávnění vyžadovaná pro sestavení spuštěn správně.  
  
 Další informace o sestavení a sestavení manifesty, naleznete v tématu [sestavení a globální mezipaměť sestavení](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).  
  
### <a name="importing-and-exporting-type-libraries"></a>Import a export knihovny typů  
 Visual Studio obsahuje nástroje, Tlbimp, který umožňuje importovat informace z knihovny typů do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikace. Knihovny typů ze sestavení můžete vygenerovat pomocí nástroje Tlbexp.  
  
 Informace o Tlbimp a Tlbexp najdete v tématu [Tlbimp.exe (Importér knihovny typů)](../../../framework/tools/tlbimp-exe-type-library-importer.md) a [Tlbexp.exe (Exportér knihovny typů)](https://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d).  
  
## <a name="interop-assemblies"></a>Sestavení vzájemné spolupráce  
 Definiční sestavení jsou [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení, která most mezi spravovaného a nespravovaného kódu, mapování členové objektu modelu COM na ekvivalentní [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] spravované členy. Definiční sestavení vytvořených pomocí jazyka Visual Basic .NET zpracování řadu podrobnosti o práci s objekty COM, jako je například zařazování vzájemná funkční spolupráce.  
  
## <a name="interoperability-marshaling"></a>Zařazování spolupráce  
 Všechny [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikace sdílet sadu běžných typů, které umožňují spolupráci objektů, bez ohledu na programovací jazyk, který se používá. Parametry a návratovými hodnotami objektů COM se někdy používají datové typy, které se liší od těch, které používají ve spravovaném kódu. *Zařazování spolupráce* při přechodu do a z objektů COM je proces balení parametry a návratové hodnoty na ekvivalentní datové typy. Další informace najdete v tématu [zařazování Interop](../../../framework/interop/interop-marshaling.md).  
  
## <a name="see-also"></a>Viz také  
 [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Návod: Implementace dědičnosti pomocí objektů COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Spolupráce s nespravovaným kódem](../../../framework/interop/index.md)  
 [Řešení potíží s interoperabilitou](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [Sestavení a globální mezipaměť sestavení (GAC)](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Tlbimp.exe (importér knihovny typů)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [Tlbexp.exe (exportér knihovny typů)](https://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [Zařazování spolupráce](../../../framework/interop/interop-marshaling.md)  
 [Bezregistrační zprostředkovatel komunikace s objekty COM](https://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)
