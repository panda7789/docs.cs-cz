---
title: Představení zprostředkovatele komunikace s objekty COM (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
ms.openlocfilehash: 5eb862d75f8870da40af4cd817fa32a3d2781f38
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592730"
---
# <a name="introduction-to-com-interop-visual-basic"></a>Představení zprostředkovatele komunikace s objekty COM (Visual Basic)
Modelu COM (Component Object) umožňuje objektu jeho funkcionalitu, ostatních komponentách a k hostování aplikací. Zatímco objekty modelu COM byly nezbytné k programování po mnoho let Windows, aplikací navržených pro modul common language runtime (CLR) nabízí celou řadu výhod.  
  
 Aplikace rozhraní .NET framework bude nakonec nahradí vyvinuté pomocí modelu COM. Dokud to neuděláte bude pravděpodobně nutné použít nebo vytvořit objekty modelu COM s použitím sady Visual Studio. Vzájemná funkční spolupráce s modelu COM, nebo *komunikace s objekty COM*, umožňuje používat stávající objekty modelu COM při přechodu na rozhraní .NET Framework svým vlastním tempem.  
  
 Vytváření komponent modelu COM pomocí rozhraní .NET Framework, můžete pomocí spolupráci s COM bez registrace. To vám umožňuje řídit, kterou verzi knihovny DLL povolíte více než jedna verze je nainstalovaná na počítači a umožňuje koncovým uživatelům pomocí příkazu XCOPY nebo FTP aplikaci do příslušného adresáře v počítači, kde lze spustit. Další informace najdete v tématu [spolupráci s COM bez registrace](../../../framework/interop/registration-free-com-interop.md).  
  
## <a name="managed-code-and-data"></a>Spravovaný kód a Data  
 Kód vyvinutý pro rozhraní .NET Framework se označuje jako *spravovaného kódu*a obsahuje metadata, která je používaná platformou CLR. Data používaná aplikací využívajících rozhraní .NET Framework se nazývá *dat spravovaných* vzhledem k tomu, že modul runtime spravuje úlohy související s daty, jako je kontrola typu přidělování a uvolní paměť a provádění. Ve výchozím nastavení Visual Basic .NET používá spravovaný kód a data, ale přístup k nespravovanému kódu a data objektů COM pomocí sestavení vzájemné spolupráce (popsaný níže na této stránce).  
  
## <a name="assemblies"></a>Sestavení  
 Sestavení je primární stavebním blokem aplikace rozhraní .NET Framework. Jde o kolekci funkcí, které jsou připravené, čísly verzí a nasazených jako jedna implementace jednotku obsahující jeden nebo více souborů. Každé sestavení obsahuje manifest sestavení.  
  
## <a name="type-libraries-and-assembly-manifests"></a>Manifesty sestavení a knihoven typů  
 Knihovny typů popisují vlastnosti objektů modelu COM, jako jsou názvy členů a datové typy. Manifesty sestavení provádí stejnou funkci pro aplikace .NET Framework. Patří mezi ně následující informace:  
  
- Identitu sestavení, verzi, jazykovou verzi a digitální podpis.  
  
- Soubory, které tvoří sestavení implementace.  
  
- Typy a prostředky, které tvoří sestavení. To zahrnuje ty, které jsou exportovány z něj.  
  
- Kompilace závislosti na ostatních sestaveních.  
  
- Oprávnění vyžadovaná pro sestavení spuštěn správně.  
  
 Další informace o sestavení a sestavení manifesty, naleznete v tématu [sestavení v rozhraní .NET](../../../standard/assembly/index.md).  
  
### <a name="importing-and-exporting-type-libraries"></a>Import a export knihovny typů  
 Visual Studio obsahuje nástroje, Tlbimp, který umožňuje importovat informace z knihovny typů do aplikace rozhraní .NET Framework. Knihovny typů ze sestavení můžete vygenerovat pomocí nástroje Tlbexp.  
  
 Informace o Tlbimp a Tlbexp najdete v tématu [Tlbimp.exe (Importér knihovny typů)](../../../framework/tools/tlbimp-exe-type-library-importer.md) a [Tlbexp.exe (Exportér knihovny typů)](../../../framework/tools/tlbexp-exe-type-library-exporter.md).  
  
## <a name="interop-assemblies"></a>Sestavení vzájemné spolupráce  
 Definiční sestavení jsou sestavení rozhraní .NET Framework, která spravují most mezi a nespravovaný kód, mapování členové objektu modelu COM na ekvivalentní rozhraní .NET Framework spravované členy. Definiční sestavení vytvořených pomocí jazyka Visual Basic .NET zpracování řadu podrobnosti o práci s objekty COM, jako je například zařazování vzájemná funkční spolupráce.  
  
## <a name="interoperability-marshaling"></a>Zařazování spolupráce  
 Všechny aplikace rozhraní .NET Framework sdílí sadu běžných typů, které umožňují spolupráci objektů, bez ohledu na programovací jazyk, který se používá. Parametry a návratovými hodnotami objektů COM se někdy používají datové typy, které se liší od těch, které používají ve spravovaném kódu. *Zařazování spolupráce* při přechodu do a z objektů COM je proces balení parametry a návratové hodnoty na ekvivalentní datové typy. Další informace najdete v tématu [zařazování Interop](../../../framework/interop/interop-marshaling.md).  
  
## <a name="see-also"></a>Viz také:

- [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Návod: Implementace dědičnosti pomocí objektů COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [Spolupráce s nespravovaným kódem](../../../framework/interop/index.md)
- [Řešení potíží s interoperabilitou](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
- [Sestavení v .NET](../../../standard/assembly/index.md)
- [Tlbimp.exe (importér knihovny typů)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (exportér knihovny typů)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [Zařazování spolupráce](../../../framework/interop/interop-marshaling.md)
- [Bezregistrační zprostředkovatel komunikace s objekty COM](../../../framework/interop/registration-free-com-interop.md)
