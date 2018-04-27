---
title: Představení zprostředkovatele komunikace s objekty COM (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5a13fabd729218dc2a980b9c63e153d17a140cce
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="introduction-to-com-interop-visual-basic"></a>Představení zprostředkovatele komunikace s objekty COM (Visual Basic)
Modelu COM (Component Object) umožňuje zpřístupnění jeho funkce pro ostatní součásti a hostování aplikací založených na objekt. Při COM – objekty byly nezbytné, aby Windows programování mnoho let, aplikací navržených pro modul CLR (CLR) nabízí celou řadu výhod.  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikace nakonec nahradí vyvinuté pomocí modelu COM. Do té doby se možná budete muset použít nebo vytvořit objekty modelu COM pomocí sady Visual Studio. Vzájemná funkční spolupráce s modelu COM, nebo *zprostředkovatel komunikace s objekty COM*, vám umožní použít při přechodu do stávajících objektů COM [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] vlastním tempem.  
  
 Pomocí [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] k vytvoření komponenty modelu COM, můžete použít spoluprací COM bez registrace. Díky tomu můžete řídit, která verze knihoven DLL je povoleno, když více než jedna verze je nainstalována v počítači a umožňuje koncovým uživatelům pomocí příkazu XCOPY nebo FTP zkopírujte vaší aplikace do příslušného adresáře v počítači, kde můžete spustit. Další informace najdete v tématu [spoluprací COM bez registrace](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd).  
  
## <a name="managed-code-and-data"></a>Spravovaný kód a Data  
 Kód vytvořených pro [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] se označuje jako *spravovaného kódu*a obsahuje metadata, která je používána modulu CLR. Data využívaná [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikacím se říká *dat spravovaných* vzhledem k tomu, že modul runtime spravuje souvisejících s daty úlohy, jako je kontrola typu přidělování a opětovného získání paměti a provádění. Ve výchozím nastavení Visual Basic .NET používá spravovaného kódu a data, ale nespravovaného kódu a data objektů modelu COM pomocí zprostředkovatele komunikace s objekty sestavení (popsané později na této stránce) jsou k dispozici.  
  
## <a name="assemblies"></a>Sestavení  
 Sestavení je primární stavebním blokem [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikace. Jedná se o kolekci funkcí, které je integrované, verzí a nasazené jako jediná implementace jednotku obsahující jeden nebo více souborů. Každé sestavení obsahuje manifest sestavení.  
  
## <a name="type-libraries-and-assembly-manifests"></a>Sestavení manifestů a knihovny typů  
 Knihovny typů popisuje vlastnosti objektů COM, jako jsou názvy členů a datové typy. Manifesty sestavení provádí stejnou funkci pro [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikace. Obsahují následující informace:  
  
-   Identita sestavení, verzi, jazykovou verzi a digitální podpis.  
  
-   Soubory, které tvoří implementace sestavení.  
  
-   Typy a prostředky, které tvoří sestavení. To zahrnuje ty, které byly exportovány z něj.  
  
-   Kompilace závislostí na ostatních sestavení.  
  
-   Oprávnění vyžadovaná pro sestavení správné fungování.  
  
 Další informace o sestavení a sestavení manifesty najdete v tématu [sestavení a globální mezipaměť sestavení](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).  
  
### <a name="importing-and-exporting-type-libraries"></a>Import a export knihovny typů  
 Obsahuje nástroje, Tlbimp, který umožňuje importovat informace z knihovny typů do sady Visual Studio [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikace. Knihovny typů ze sestavení můžete vygenerovat pomocí nástroje Tlbexp.  
  
 Informace o Tlbimp a Tlbexp najdete v tématu [Tlbimp.exe (Importér knihovny)](../../../framework/tools/tlbimp-exe-type-library-importer.md) a [Tlbexp.exe (Exportér knihovny)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d).  
  
## <a name="interop-assemblies"></a>Sestavení spolupráce  
 Spolupráce – sestavení jsou [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení, které most mezi spravovaných a nespravovaných code, členové objektu COM mapování na ekvivalentní [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] spravované členy. Spolupráce – sestavení vytvořené Visual Basic .NET zpracovávat řadu podrobnosti o práci s objekty modelu COM, jako je například zařazování interoperability.  
  
## <a name="interoperability-marshaling"></a>Zařazování spolupráce  
 Všechny [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikace sdílet sadu běžné typy, které umožňuje interoperabilitu objektů, bez ohledu na programovací jazyk, který se používá. Parametry a návratové hodnoty objektů COM někdy použít datové typy, které se liší od těch, které používá ve spravovaném kódu. *Vzájemná funkční spolupráce zařazování* je proces balení parametry a návratové hodnoty do ekvivalentní datové typy, jako se přesouvají do a z COM – objekty. Další informace najdete v tématu [zařazování zprostředkovatel komunikace s objekty](../../../framework/interop/interop-marshaling.md).  
  
## <a name="see-also"></a>Viz také  
 [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Návod: Implementace dědičnosti pomocí objektů COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Spolupráce s nespravovaným kódem](../../../framework/interop/index.md)  
 [Řešení potíží s interoperabilitou](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [Sestavení a globální mezipaměť sestavení (GAC)](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Tlbimp.exe (importér knihovny typů)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [Tlbexp.exe (exportér knihovny typů)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [Zařazování spolupráce](../../../framework/interop/interop-marshaling.md)  
 [Bezregistrační zprostředkovatel komunikace s objekty COM](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)
