---
title: WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) – metoda
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
api_name:
- System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream
api_location:
- System.Runtime.WindowsRuntime.dll
ms.assetid: dcc72283-caed-49ee-b45d-ccaf94e97129
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d5dd2829a9a00f869af3d7f370f99361979b8106
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921313"
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a>WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) – metoda

[Podporované v rozhraní .NET Framework 4.5.1 a novějších verzích]

Převede zadaný datový proud na datový proud s náhodným přístupem.

**Namespace:** <xref:System.IO?displayProperty=nameWithType>
**Sestavení:** System.Runtime.WindowsRuntime (v souboru System.Runtime.WindowsRuntime.dll)

## <a name="syntax"></a>Syntaxe

```csharp
[CLSCompliantAttribute(false)]
public static IRandomAccessStream AsRandomAccessStream(Stream stream)
```

```vb
'Declaration
<ExtensionAttribute> _
<CLSCompliantAttribute(False)> _
Public Shared Function AsRandomAccessStream ( _
        stream As Stream) As IRandomAccessStream
```

## <a name="parameters"></a>Parametry

`stream`

Typ: <xref:System.IO.Stream?displayProperty=nameWithType>  
Datový proud, který chcete převést.

## <a name="return-value"></a>Návratová hodnota

Typ: <xref:Windows.Storage.Streams.RandomAccessStream>  
A [!INCLUDE[wrt](../../../includes/wrt-md.md)] stream náhodný přístup, který představuje převedený datový proud.

## <a name="exceptions"></a>Výjimky

|Výjimka|Podmínka|
|---------------|---------------|
|<xref:System.NotSupportedException>|Datový proud, který chcete převést, nepodporuje vyhledávání.|

## <a name="remarks"></a>Poznámky

Tato metoda rozšíření je k dispozici pouze v případě, že vyvíjíte aplikace pro Windows Store. Tato metoda poskytuje pohodlný způsob práce s datovými proudy v aplikacích pro Windows Store. Datový proud rozhraní .NET Framework, kterou chcete převést, musí podporovat vyhledávání. Další informace najdete v tématu <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> metody.

> [!IMPORTANT]
> Toto rozhraní API je podporováno v rozhraní .NET Framework 4.5.1 a novější verze, ale ne ve verzi 4.5.

## <a name="version-information"></a>Informace o verzi

**.NET pro aplikace Windows Store**

Podporované v: Windows 8.1

## <a name="see-also"></a>Viz také:

- [Postupy: Převod mezi streamy rozhraní .NET Framework a datovými proudy Windows Runtime](../io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
