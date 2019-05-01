---
title: Interoperabilita modelů COM v aplikacích .NET Framework (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
ms.openlocfilehash: 6e8b4eba40cc1872cb289ca120679bb951f2652a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022374"
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>Interoperabilita modelů COM v aplikacích .NET Framework (Visual Basic)

Pokud chcete použít objekty COM a rozhraní .NET Framework ve stejné aplikaci, budete muset vyřešit rozdíly v tom, jak objekty existují v paměti. Objekt rozhraní .NET Framework je umístěn ve spravované paměti – paměť řídí modul common language runtime a podle potřeby, mohou být přesunuty modulem runtime. Objekt modelu COM je umístěn v nespravované paměti a neočekává se přesunout do jiného umístění v paměti. Visual Studio a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] poskytují nástroje pro řízení interakce z nich spravované a nespravované součásti. Další informace o spravovaném kódu najdete v tématu [Common Language Runtime](../../../standard/clr.md).

Kromě použití objektů COM v aplikacích .NET, můžete také pomocí jazyka Visual Basic k vývoji objekty přístupné z nespravovaného kódu pomocí modelu COM.

Odkazy na této stránce poskytují podrobné informace o interakcích mezi objekty modelu COM a rozhraní .NET Framework.

## <a name="related-sections"></a>Související oddíly

| | |
|---------|---------|
| [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md) | Obsahuje odkazy na témata týkající se interoperabilita modelů COM v jazyce Visual Basic, včetně modelu COM objekty ActiveX ovládací prvky, knihovnami DLL Win32, spravované objekty a dědičnosti objektů modelu COM. |
| [Spolupráce s nespravovaným kódem](../../../framework/interop/index.md) | Stručně popisuje některé z problémů interakce mezi spravovaným a nespravovaným kódem a obsahuje odkazy na další studie. |
| [COM – obálky](../../../framework/interop/com-wrappers.md) | Tento článek popisuje obálek volatelných za běhu, které umožňují spravovanému kódu volat metody modelu COM, a obálky volatelné modelem COM, které umožní klientům modelu COM, volání metod objekt .NET. |
| [Rozšířená interoperabilita modelu COM](../../../framework/interop/index.md) | Obsahuje odkazy na témata týkající se vzájemná funkční spolupráce modelu COM s ohledem na obálky, výjimky, dědičnost, práce s vlákny, události, převody a zařazování. |
| [Tlbimp.exe (importér knihovny typů)](../../../framework/tools/tlbimp-exe-type-library-importer.md) | Tento článek popisuje nástroje, které lze použít k převodu definice typu nalezené v knihovně typů modelu COM na ekvivalentní definice v sestavení common language runtime. |