---
title: Interoperabilita modelů COM v aplikacích .NET Framework (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
ms.openlocfilehash: ceef4255321e208911a16db0227890bc6654b8c5
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244661"
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>Interoperabilita modelů COM v aplikacích .NET Framework (Visual Basic)
Pokud chcete použít objekty COM a rozhraní .NET Framework ve stejné aplikaci, budete muset vyřešit rozdíly v tom, jak objekty existují v paměti. Objekt rozhraní .NET Framework je umístěn ve spravované paměti – paměť řídí modul common language runtime a podle potřeby, mohou být přesunuty modulem runtime. Objekt modelu COM je umístěn v nespravované paměti a neočekává se přesunout do jiného umístění v paměti. Visual Studio a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] poskytují nástroje pro řízení interakce z nich spravované a nespravované součásti. Další informace o spravovaném kódu najdete v tématu [Common Language Runtime](../../../standard/clr.md).  
  
 Kromě použití objektů COM v aplikacích .NET, můžete také pomocí jazyka Visual Basic k vývoji objekty přístupné z nespravovaného kódu pomocí modelu COM.  
  
 Odkazy na této stránce poskytují podrobné informace o interakcích mezi objekty modelu COM a rozhraní .NET Framework.  
  
## <a name="related-sections"></a>Související oddíly  
 [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 Obsahuje odkazy na témata týkající se interoperabilita modelů COM v jazyce Visual Basic, včetně modelu COM objekty ActiveX ovládací prvky, knihovnami DLL Win32, spravované objekty a dědičnosti objektů modelu COM.  
  
 [Chyba obálku vzájemné spolupráce COM](/cpp/misc/com-interop-wrapper-error)  
 Popisuje důsledky a možnosti, pokud systém projektu nemůže vytvořit obálku vzájemná funkční spolupráce modelu COM pro konkrétní komponentu.  
  
 [Spolupráce s nespravovaným kódem](../../../framework/interop/index.md)  
 Stručně popisuje některé z problémů interakce mezi spravovaným a nespravovaným kódem a obsahuje odkazy na další studie.  
  
 [COM – obálky](../../../framework/interop/com-wrappers.md)  
 Tento článek popisuje obálek volatelných za běhu, které umožňují spravovanému kódu volat metody modelu COM, a obálky volatelné modelem COM, které umožní klientům modelu COM, volání metod objekt .NET.  
  
 [Rozšířená interoperabilita modelu COM](../../../framework/interop/index.md)  
 Obsahuje odkazy na témata týkající se vzájemná funkční spolupráce modelu COM s ohledem na obálky, výjimky, dědičnost, práce s vlákny, události, převody a zařazování.  
  
 [Tlbimp.exe (importér knihovny typů)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 Tento článek popisuje nástroje, které lze použít k převodu definice typu nalezené v knihovně typů modelu COM na ekvivalentní definice v sestavení common language runtime.
