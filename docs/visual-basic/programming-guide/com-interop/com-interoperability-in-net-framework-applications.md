---
title: Interoperabilita modelů COM v aplikacích .NET Framework
ms.date: 07/20/2015
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
ms.openlocfilehash: 1c484ae948c247a97dd57539e3b0be263736aceb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348750"
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>Interoperabilita modelů COM v aplikacích .NET Framework (Visual Basic)

Pokud chcete použít objekty COM a .NET Framework objekty ve stejné aplikaci, je nutné vyřešit rozdíly ve způsobu, jakým objekty existují v paměti. Objekt .NET Framework je umístěn ve spravované paměti – paměť řízená modulem CLR (Common Language Runtime) a může být v případě potřeby přesunuta podle potřeby za běhu. Objekt COM je umístěný v nespravované paměti a neočekává se přesun do jiného umístění v paměti. Visual Studio a .NET Framework poskytují nástroje pro řízení interakce těchto spravovaných a nespravovaných komponent. Další informace o spravovaném kódu naleznete v tématu [Common Language Runtime](../../../standard/clr.md).

Kromě používání objektů COM v aplikacích .NET můžete také použít Visual Basic pro vývoj objektů přístupných z nespravovaného kódu pomocí modelu COM.

Odkazy na této stránce poskytují podrobné informace o interakcích mezi objekty COM a .NET Framework.

## <a name="related-sections"></a>Související oddíly

| | |
|---------|---------|
| [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md) | Obsahuje odkazy na témata týkající se interoperability modelu COM v Visual Basic, včetně objektů COM, ovládacích prvků ActiveX, knihoven DLL Win32, spravovaných objektů a dědičnosti objektů COM. |
| [Spolupráce s nespravovaným kódem](../../../framework/interop/index.md) | Stručně popisuje některé problémy interakce mezi spravovaným a nespravovaným kódem a poskytuje odkazy k další studiu. |
| [COM – obálky](../../../standard/native-interop/com-wrappers.md) | Popisuje obálky s voláním za běhu, které umožňují spravovanému kódu volat metody modelu COM a obálky s možnostmi volání modelu COM, které umožňují klientům modelu COM volat metody objektů .NET. |
| [Pokročilá interoperabilita modelu COM](../../../framework/interop/index.md) | Obsahuje odkazy na témata týkající se interoperability modelu COM v souvislosti s obálkami, výjimkami, dědičností, vlákny, událostmi, převody a zařazováním. |
| [Tlbimp.exe (importér knihovny typů)](../../../framework/tools/tlbimp-exe-type-library-importer.md) | Popisuje nástroj, který můžete použít k převedení definic typů nalezených v knihovně typů modelu COM na ekvivalentní definice v sestavení společného jazykového modulu runtime. |
