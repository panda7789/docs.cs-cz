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
ms.openlocfilehash: a712414163446606cbc93154bc821d3b1166fe8f
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43254254"
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a>WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) – metoda

[Podporované v rozhraní .NET Framework 4.5.1 a novějších verzích]

Převede zadaný datový proud na datový proud s náhodným přístupem.

**Namespace:** <xref:System.IO?displayProperty=nameWithType> 
 **sestavení:** System.Runtime.WindowsRuntime (v souboru System.Runtime.WindowsRuntime.dll)

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

Podporováno v systému: Windows 8.1

## <a name="see-also"></a>Viz také

[System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions(v=vs.110).aspx)  
[Postupy: Převádění mezi streamy rozhraní .NET Framework a streamy prostředí Windows Runtime](../io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  