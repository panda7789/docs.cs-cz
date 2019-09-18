---
title: Přenositelné a nepřenositelné typy
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 739f0efdb50f8eba4875a42d5173f741b6ee94b3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051888"
---
# <a name="blittable-and-non-blittable-types"></a>Přenositelné a nepřenositelné typy
Většina datových typů má společné vyjádření ve spravované i nespravované paměti a nevyžaduje speciální zpracování v zařazovací službě Interop. Tyto typy se nazývají přenositelné *typy* , protože nevyžadují převod, pokud jsou předávány mezi spravovaným a nespravovaným kódem.  
  
 Struktury, které jsou vraceny voláními vyvolání platformy musí být typu přenositelné. Vyvolání platformy nepodporuje struktury, které nejsou přenositelné jako návratové typy.  
  
 Následující typy z <xref:System> oboru názvů jsou přenositelné typy:  
  
- <xref:System.Byte?displayProperty=nameWithType>  
  
- <xref:System.SByte?displayProperty=nameWithType>  
  
- <xref:System.Int16?displayProperty=nameWithType>  
  
- <xref:System.UInt16?displayProperty=nameWithType>  
  
- <xref:System.Int32?displayProperty=nameWithType>  
  
- <xref:System.UInt32?displayProperty=nameWithType>  
  
- <xref:System.Int64?displayProperty=nameWithType>  
  
- <xref:System.UInt64?displayProperty=nameWithType>  
  
- <xref:System.IntPtr?displayProperty=nameWithType>  
  
- <xref:System.UIntPtr?displayProperty=nameWithType>  
  
- <xref:System.Single?displayProperty=nameWithType>  
  
- <xref:System.Double?displayProperty=nameWithType>  
  
 Následující komplexní typy jsou také přenositelné typy:  
  
- Jednorozměrná pole typů s více typy, jako je například pole celých čísel. Typ, který obsahuje proměnné pole typu, však není přímo přenositelný.  
  
- Formátované typy hodnot, které obsahují pouze přenositelné typy (a třídy, pokud jsou zařazeny jako formátované typy). Další informace o formátovaných hodnotových typech naleznete v tématu [Výchozí zařazování pro typy hodnot](default-marshaling-behavior.md#default-marshaling-for-value-types).  
  
 Odkazy na objekty nejsou nanositelné. To zahrnuje pole odkazů na objekty, které jsou přímo přenositelně. Můžete například definovat strukturu, která je přenositelná, ale nelze definovat typ přenositeli, který obsahuje pole odkazů na tyto struktury.  
  
 V rámci optimalizace se při zařazování [připnuté](copying-and-pinning.md) pole typů a tříd, které obsahují pouze Nepřenositelný člen, se místo kopírování. Tyto typy mohou být zařazeny jako vstupně-výstupní parametry, pokud jsou volající a volaný ve stejném typu apartment. Tyto typy jsou však ve skutečnosti zařazeny jako v parametrech a je nutné použít <xref:System.Runtime.InteropServices.InAttribute> atributy a <xref:System.Runtime.InteropServices.OutAttribute> , pokud chcete zařadit argument jako vstupně-výstupní parametr.  
  
 Některé spravované datové typy vyžadují jiné reprezentace v nespravovaném prostředí. Tyto nepřenosné datové typy musí být převedeny do formuláře, který lze zařadit. Například spravované řetězce jsou nepřenositelné typy, protože musí být převedeny na řetězcové objekty předtím, než mohou být zařazeny do objektů typu String.  
  
 V následující tabulce jsou uvedeny nepřenositelné typy z <xref:System> oboru názvů. [Delegáti](default-marshaling-behavior.md#default-marshaling-for-delegates), což jsou datové struktury, které odkazují na statickou metodu nebo na instanci třídy, jsou také nepřímo přenositelná.  
  
|Netypový typ|Popis|  
|-------------------------|-----------------|  
|[System.Array](default-marshaling-for-arrays.md)|Převede na pole ve stylu jazyka C nebo `SAFEARRAY`.|  
|[System.Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))|Převede na hodnotu 1, 2 nebo 4 bajty s `true` hodnotou 1 nebo-1.|  
|[System.Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))|Převede na znak Unicode nebo ANSI.|  
|[System.Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))|Převede na rozhraní třídy.|  
|[System. Object](default-marshaling-for-objects.md)|Převede na typ variant nebo rozhraní.|  
|[System.Mdarray](default-marshaling-for-arrays.md)|Převede na pole ve stylu jazyka C nebo `SAFEARRAY`.|  
|[System. String](default-marshaling-for-strings.md)|Převede na řetězec ukončující v odkazu s hodnotou null nebo na BSTR.|  
|[System. ValueType](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))|Převede se na strukturu s pevným rozložením paměti.|  
|[System.Szarray](default-marshaling-for-arrays.md)|Převede na pole ve stylu jazyka C nebo `SAFEARRAY`.|  
  
 Typy tříd a objektů jsou podporovány pouze zprostředkovatelem komunikace s objekty COM. Pro odpovídající typy v Visual Basic, C#a C++, viz [Přehled knihovny tříd](../../standard/class-library-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Výchozí chování zařazování](default-marshaling-behavior.md)
