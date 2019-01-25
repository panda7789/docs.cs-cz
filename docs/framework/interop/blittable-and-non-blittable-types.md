---
title: Přenositelné a nepřenositelné typy
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ce1c944257a1a11287b751d9a0f9eb5a88d744f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596888"
---
# <a name="blittable-and-non-blittable-types"></a>Přenositelné a nepřenositelné typy
Většina datových typů mají společné reprezentaci ve spravované i nespravované paměti a nevyžadují žádná zvláštní zacházení podle interoperační zařazovač. Tyto typy jsou označovány jako *přenositelné typy* vzhledem k tomu, že když jsou předávány mezi nevyžadují převod spravovaného a nespravovaného kódu.  
  
 Struktury, které jsou vráceny z platformy vyvolat volání musí být přenositelné typy. Vyvolání platformy nepodporuje nepřenositelné struktury jako typy vracených hodnot.  
  
 Následující typy <xref:System> obor názvů jsou přenositelné typy:  
  
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
  
-   Jednorozměrná pole přenositelné typy, jako je například pole celých čísel. Ale typ, který obsahuje proměnné pole přenositelné typy není samotného typu blittable.  
  
-   Formátovaná hodnota typy, které obsahují pouze přenositelné typy (a třídy, pokud jsou zařazeny jako formátovaný typy). Další informace o typech formátovaná hodnota najdete v tématu [výchozí zařazování pro typy hodnot](https://msdn.microsoft.com/library/4d9a876c-e05a-40ba-bd85-bd22877f984a(v=vs.100)).  
  
 Odkazy na objekty nejsou typu blittable. To zahrnuje pole odkazů na objekty, které jsou přenositelné samy o sobě. Například můžete definovat strukturu, která je typu blittable, ale nelze definovat typu blittable, který obsahuje pole odkazů na tyto struktury.  
  
 Optimalizace, jsou pole přenositelné typy a třídy, které obsahují pouze členy typu blittable [připnuté](../../../docs/framework/interop/copying-and-pinning.md) místo zkopírovaných při zařazování. Tyto typy může zdát zařadit jako vstup a výstup parametry při volajícím a volaným jsou ve stejném objektu apartment. Ale tyto typy jsou ve skutečnosti zařadit jako parametry in a je nutné použít <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute> atributy, pokud chcete zařadit argument jako vstupně -výstupní parametr.  
  
 Některé spravované datové typy vyžadují různé reprezentace v nespravované prostředí. Tyto nepřenositelné typy dat musí být převeden do formuláře, který může být zařazována. Například spravované řetězce jsou nepřenositelné typy, protože je potřeba je převést na řetězec objekty předtím, než může být zařazována.  
  
 V následující tabulce jsou uvedeny nepřenositelné typy z <xref:System> oboru názvů. [Delegáti](https://msdn.microsoft.com/library/d176ee76-f982-494b-b03d-92e4118896e2(v=vs.100)), které jsou datové struktury, které odkazují na statickou metodu nebo instanci třídy jsou také nepřenositelná.  
  
|Přenositelné bez typu|Popis|  
|-------------------------|-----------------|  
|[System.Array](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Převede pole stylu C nebo `SAFEARRAY`.|  
|[System.Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))|Převede na 1, 2 nebo 4 bajty hodnoty s `true` jako 1 nebo -1.|  
|[System.Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))|Převede znak Unicode nebo ANSI.|  
|[System.Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))|Převede na třídy rozhraní.|  
|[System.Object](../../../docs/framework/interop/default-marshaling-for-objects.md)|Převede hodnotu typu variant nebo rozhraní.|  
|[System.Mdarray](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Převede pole stylu C nebo `SAFEARRAY`.|  
|[System.String](../../../docs/framework/interop/default-marshaling-for-strings.md)|Převede řetězec ukončení v odkaz s hodnotou null nebo BSTR.|  
|[Typ System.Valuetype](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))|Převede na strukturu s rozložením pevné paměti.|  
|[System.Szarray](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Převede pole stylu C nebo `SAFEARRAY`.|  
  
 Typy tříd a objektů jsou podporovány pouze komunikace s objekty COM. Pro odpovídající typy v [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#a C++, naleznete v tématu [– přehled knihovny tříd](../../../docs/standard/class-library-overview.md).  
  
## <a name="see-also"></a>Viz také:
- [Výchozí chování zařazování](../../../docs/framework/interop/default-marshaling-behavior.md)
