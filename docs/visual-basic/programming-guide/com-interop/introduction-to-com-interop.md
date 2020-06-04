---
title: Představení zprostředkovatele komunikace s objekty COM
ms.date: 07/20/2015
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
ms.openlocfilehash: 6c7caf266514c43e40135b33d848a688546acf1c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396776"
---
# <a name="introduction-to-com-interop-visual-basic"></a>Představení zprostředkovatele komunikace s objekty COM (Visual Basic)
Model objektu komponenty (COM) umožňuje objektu vystavit svou funkčnost jiným komponentám a hostovat aplikace. I když byly objekty COM zásadní pro programování v systému Windows po celou řadu let, aplikace navržené pro modul CLR (Common Language Runtime) nabízejí mnoho výhod.  
  
 Aplikace .NET Framework nakonec nahradí ta vyvinutá pomocí modelu COM. Do té doby bude pravděpodobně nutné použít nebo vytvořit objekty COM pomocí sady Visual Studio. Interoperabilita s COM nebo *zprostředkovatelem komunikace s objekty*com umožňuje používat existující objekty COM při přechodu na .NET Framework vlastním tempem.  
  
 Pomocí .NET Framework k vytváření komponent modelu COM můžete použít zprostředkovatele komunikace COM bez registrace. To vám umožňuje řídit, která verze knihovny DLL je povolena, pokud je v počítači nainstalována více než jedna verze a umožňuje koncovým uživatelům zkopírovat aplikaci do příslušného adresáře na svém počítači, kde je lze spustit. Další informace najdete v tématu [komunikace s objekty COM bez registrace](../../../framework/interop/registration-free-com-interop.md).  
  
## <a name="managed-code-and-data"></a>Spravovaný kód a data  
 Kód vyvinutý pro .NET Framework je označován jako *spravovaný kód*a obsahuje metadata, která jsou používána modulem CLR. Data používaná aplikacemi .NET Framework se nazývají *spravovaná data* , protože modul runtime spravuje úlohy související s daty, jako je přidělení a uvolnění paměti a provádění kontroly typu. Ve výchozím nastavení používá Visual Basic .NET spravovaný kód a data, ale můžete získat přístup k nespravovanému kódu a datům objektů COM pomocí definičních sestavení (popsaných dále na této stránce).  
  
## <a name="assemblies"></a>Sestavení  
 Sestavení je primární stavební blok aplikace .NET Framework. Je to kolekce funkcí, která je sestavená a nasazená jako jediná jednotka implementace obsahující jeden nebo více souborů. Každé sestavení obsahuje manifest sestavení.  
  
## <a name="type-libraries-and-assembly-manifests"></a>Knihovny typů a manifesty sestavení  
 Knihovny typů popisují charakteristiky objektů COM, jako jsou názvy členů a datové typy. Manifesty sestavení provádějí stejnou funkci pro .NET Framework aplikace. Obsahují informace o následujícím:  
  
- Identita sestavení, verze, jazyková verze a digitální podpis.  
  
- Soubory, které tvoří implementaci sestavení.  
  
- Typy a prostředky, které tvoří sestavení. To zahrnuje ty, které se z něho exportují.  
  
- Závislosti v čase kompilace na jiných sestaveních.  
  
- Oprávnění požadovaná pro správné spuštění sestavení.  
  
 Další informace o sestaveních a manifestech sestavení naleznete [v tématu sestavení v rozhraní .NET](../../../standard/assembly/index.md).  
  
### <a name="importing-and-exporting-type-libraries"></a>Import a export knihoven typů  
 Visual Studio obsahuje nástroj Tlbimp, který umožňuje importovat informace z knihovny typů do .NET Framework aplikace. Knihovny typů můžete generovat ze sestavení pomocí nástroje Tlbexp.  
  
 Informace o Tlbimp a Tlbexp naleznete v tématu [Tlbimp. exe (import knihovny typů)](../../../framework/tools/tlbimp-exe-type-library-importer.md) a [Tlbexp. exe (typ Exportér knihovny typů)](../../../framework/tools/tlbexp-exe-type-library-exporter.md).  
  
## <a name="interop-assemblies"></a>Definiční sestavení  
 Sestavení spolupráce jsou .NET Framework sestavení, která přecházejí mezi spravovaným a nespravovaným kódem, mapováním členů objektu COM na ekvivalentní .NET Framework spravovaných členů. Sestavení spolupráce vytvořená Visual Basic .NET zpracovávají mnoho podrobností o práci s objekty COM, jako je zařazování interoperability.  
  
## <a name="interoperability-marshaling"></a>Zařazování interoperability  
 Všechny aplikace .NET Framework sdílejí sadu běžných typů, které umožňují vzájemnou funkční spolupráci objektů bez ohledu na použitý programovací jazyk. Parametry a návratové hodnoty objektů COM někdy používají datové typy, které se liší od těch, které jsou používány ve spravovaném kódu. *Zařazování interoperability* je proces sbalení parametrů a návratové hodnoty do ekvivalentních datových typů při jejich přesunu do objektů COM a z nich. Další informace najdete v tématu [zařazování Interop](../../../framework/interop/interop-marshaling.md).  
  
## <a name="see-also"></a>Viz také

- [Zprostředkovatel komunikace s objekty COM](index.md)
- [Návod: Implementace dědičnosti pomocí objektů COM](walkthrough-implementing-inheritance-with-com-objects.md)
- [Spolupráce s nespravovaným kódem](../../../framework/interop/index.md)
- [Řešení potíží s interoperabilitou](troubleshooting-interoperability.md)
- [Sestavení v .NET](../../../standard/assembly/index.md)
- [Tlbimp. exe (importér knihovny typů)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp. exe (Exportér knihovny typů)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [Zařazování spolupráce](../../../framework/interop/interop-marshaling.md)
- [Zprostředkovatel komunikace s objekty COM bez registrace](../../../framework/interop/registration-free-com-interop.md)
