---
title: "Přenositelné a nepřenositelné typy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b05d77df28b560b9236e467a914229c0fa9ae7e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="blittable-and-non-blittable-types"></a>Přenositelné a nepřenositelné typy
Většina typy dat mají společné reprezentaci v spravované i nespravované paměti a nevyžadují žádná zvláštní zpracování pomocí zprostředkovatele komunikace s objekty vláken. Tyto typy jsou označovány jako *přenositelné typy* vzhledem k tomu, že jsou předávány mezi nevyžadují převodu spravovaných a nespravovaných kódu.  
  
 Struktury, které jsou vráceny z platformy vyvolat volání musí být přenositelné typy. Vyvolání platformy nepodporuje nepřenositelné struktury jako návratové typy.  
  
 Následující typy z <xref:System> obor názvů jsou přenositelné typy:  
  
-   <xref:System.Byte?displayProperty=nameWithType>  
  
-   <xref:System.SByte?displayProperty=nameWithType>  
  
-   <xref:System.Int16?displayProperty=nameWithType>  
  
-   <xref:System.UInt16?displayProperty=nameWithType>  
  
-   <xref:System.Int32?displayProperty=nameWithType>  
  
-   <xref:System.UInt32?displayProperty=nameWithType>  
  
-   <xref:System.Int64?displayProperty=nameWithType>  
  
-   <xref:System.UInt64?displayProperty=nameWithType>  
  
-   <xref:System.IntPtr?displayProperty=nameWithType>  
  
-   <xref:System.UIntPtr?displayProperty=nameWithType>  
  
-   <xref:System.Single?displayProperty=nameWithType>  
  
-   <xref:System.Double?displayProperty=nameWithType>  
  
 Přenositelné typy jsou také následující komplexní typy:  
  
-   Jednorozměrná pole přenositelné typy, jako je například pole celých čísel. Typ, který obsahuje proměnné pole přenositelné typy není však samotné přenositelné.  
  
-   Formátovaná hodnota typů, které obsahují pouze přenositelné typy (a třídy, pokud jsou zařazené jako formátovaný typy). Další informace o typech formátovanou hodnotu najdete v tématu [výchozí zařazování pro typy hodnot](http://msdn.microsoft.com/en-us/4d9a876c-e05a-40ba-bd85-bd22877f984a).  
  
 Odkazy na objekty nejsou typu blittable. To zahrnuje pole odkazy na objekty, které jsou přenositelné samy o sobě. Například můžete definovat strukturu, která je typu blittable, ale nelze definovat typu blittable, který obsahuje řadu odkazů na tyto struktury.  
  
 Jako optimalizace, pole přenositelné typy a tříd, které obsahují pouze přenositelné členové jsou [připnutý](../../../docs/framework/interop/copying-and-pinning.md) místo zkopírovaných při zařazování. Tyto typy se může zobrazit být zařazena jako vstupně -výstupní parametry, pokud jsou volající a volaný ve stejném typu apartment. Ale tyto typy jsou ve skutečnosti zařazené jako parametry, a je nutné použít <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute> atributy, pokud chcete zařazování argument jako ve vstupně -výstupnímu parametru.  
  
 Některé spravované datové typy vyžadují různé reprezentace v nespravované prostředí. Tyto datové typy nepřenositelné musí být převedeny na formulář, který může být zařazen. Například spravované řetězce jsou nepřenositelné typy, protože se musí před převést do řetězce objekty může být zařazeno.  
  
 Následující tabulka uvádí nepřenositelné typy z <xref:System> oboru názvů. [Delegáti](http://msdn.microsoft.com/en-us/d176ee76-f982-494b-b03d-92e4118896e2), které jsou datové struktury, které odkazují na statickou metodu nebo instanci třídy jsou také nepřenositelné.  
  
|Přenositelné bez typu|Popis|  
|-------------------------|-----------------|  
|[System.Array](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Převede pole stylu jazyka C nebo `SAFEARRAY`.|  
|[System.Boolean](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)|Převede na 1, 2 nebo 4 bajtů hodnotu s `true` -1 nebo 1.|  
|[System.Char](http://msdn.microsoft.com/en-us/cecc87c1-075e-4cde-aa56-33d189f66feb)|Převede na znak Unicode nebo ANSI.|  
|[System.Class](http://msdn.microsoft.com/en-us/fe334af5-0123-43d8-be84-26f6f023ddb6)|Převede na třídu rozhraní.|  
|[System.Object](../../../docs/framework/interop/default-marshaling-for-objects.md)|Převede hodnotu typu variant nebo rozhraní.|  
|[System.Mdarray](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Převede pole stylu jazyka C nebo `SAFEARRAY`.|  
|[System.String](../../../docs/framework/interop/default-marshaling-for-strings.md)|Převede řetězec ukončuje v odkaz s hodnotou null nebo BSTR.|  
|[Typ System.Valuetype](http://msdn.microsoft.com/en-us/4d9a876c-e05a-40ba-bd85-bd22877f984a)|Převede na struktura s pevnou paměti rozložení.|  
|[System.Szarray](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Převede pole stylu jazyka C nebo `SAFEARRAY`.|  
  
 Typy tříd a objektů jsou podporovány pouze zprostředkovatel komunikace s objekty COM. Pro odpovídající typy v [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# a C++, najdete [– přehled knihovny tříd](../../../docs/standard/class-library-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Výchozí chování zařazování](../../../docs/framework/interop/default-marshaling-behavior.md)
