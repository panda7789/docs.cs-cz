---
title: Interoperabilita modelů COM v aplikacích .NET Framework (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
ms.openlocfilehash: 758f065d2e0e7f8200529ef171dc89f94950b46e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627088"
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
