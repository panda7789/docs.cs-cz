---
title: "Interoperabilita modelů COM v aplikacích .NET Framework (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 28ec54dc062d4fdea4836b0ecc8699982dace623
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>Interoperabilita modelů COM v aplikacích .NET Framework (Visual Basic)
Pokud chcete použít objekty COM a .NET Framework objekty ve stejné aplikaci, budete muset vyřešit rozdíly v tom, jak existují objekty v paměti. Objekt rozhraní .NET Framework je umístěn ve spravované paměti – paměť řízené modul common language runtime – a může podle potřeby přesunout modulem runtime. Objekt COM se nachází v nespravované paměti a neočekává přesunout do jiného umístění v paměti. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] poskytují nástroje pro řízení interakce těchto spravovaných a nespravovaných součásti. Další informace o spravovaném kódu najdete v tématu [modul Common Language Runtime](../../../standard/clr.md).  
  
 Kromě použití objektů COM v aplikacích .NET, můžete také použít [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] vyvíjet objekty, které jsou přístupné z nespravovaného kódu pomocí modelu COM.  
  
 Odkazy na této stránce obsahují podrobné informace o interakcích mezi objekty modelu COM a .NET Framework.  
  
## <a name="related-sections"></a>Související oddíly  
 [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 Obsahuje odkazy na témata týkající se interoperabilita modelů COM v jazyce Visual Basic, včetně COM objekty, ActiveX – ovládací prvky, knihovny DLL Win32, spravované objekty a dědičnosti objektů COM.  
  
 [Chyba obálky zprostředkovatele komunikace s objekty COM](/cpp/misc/com-interop-wrapper-error)  
 Popisuje důsledky a možnosti, pokud systém projektu nelze vytvořit obálku vzájemná funkční spolupráce COM pro konkrétní součást.  
  
 [Spolupráce s nespravovaným kódem](../../../../docs/framework/interop/index.md)  
 Stručně popisuje některé z potíží interakce mezi spravovanými a nespravovanými kódu a obsahuje odkazy na další studie.  
  
 [COM – obálky](../../../framework/interop/com-wrappers.md)  
 Popisuje běhové obálky s možností, které umožňují spravovaného kódu k volání metody modelu COM, a COM – obálky s možností, které klientům COM k volání metody objekt .NET.  
  
 [Interoperabilita modelů COM Upřesnit](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 Obsahuje odkazy na témata týkající se funkční spolupráce COM s ohledem na obálky, výjimky, dědičnosti, dělení na vlákna, události, převody a zařazování.  
  
 [Tlbimp.exe (Importér knihovny)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 Popisuje nástroje, které můžete použít pro převod definic typů v rámci knihovny typů COM nalezen do ekvivalentní definice v běžné sestavení modulu runtime jazyka.
