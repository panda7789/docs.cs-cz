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
ms.openlocfilehash: 16f878abc11589fe62f78d941b367d82d7b49e1c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a>WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) – metoda
[Podporované v rozhraní .NET Framework 4.5.1 a novějších verzích]  
  
 Převede zadaný datový proud na datový proud s náhodným přístupem.  
  
 **Namespace:** <xref:System.IO?displayProperty=nameWithType>  
 **Sestavení:** System.Runtime.WindowsRuntime (v System.Runtime.WindowsRuntime.dll)  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
[CLSCompliantAttribute(false)]  
public static  IRandomAccessStream AsRandomAccessStream(Stream stream)  
```  
  
```vb  
'Declaration  
<ExtensionAttribute> _  
<CLSCompliantAttribute(False)> _  
Public Shared Function AsRandomAccessStream ( _  
        stream As Stream) As IRandomAccessStream  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
  
 Typ: <xref:System.IO.Stream?displayProperty=nameWithType>  
Datový proud, který chcete převést.  
  
## <a name="return-value"></a>Návratová hodnota  
 Typ: [Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)  
A [!INCLUDE[wrt](../../../includes/wrt-md.md)] náhodný přístup datový proud, který představuje převedenou datového proudu.  
  
## <a name="exceptions"></a>Výjimky  
  
|Výjimka|Podmínka|  
|---------------|---------------|  
|<xref:System.NotSupportedException>|Datový proud, který chcete převést, nepodporuje vyhledávání.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda rozšíření je k dispozici pouze v případě, že vyvíjíte aplikace pro Windows Store. Tato metoda poskytuje pohodlný způsob práce s datovými proudy v aplikacích pro Windows Store. Datový proud rozhraní .NET Framework, který chcete převést musí podporovat hledání pozice. Další informace najdete v tématu <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> metoda.  
  
> [!IMPORTANT]
>  Toto rozhraní API je podporována v rozhraní .NET Framework 4.5.1 a novějších verzích, ale není v verze 4.5.  
  
## <a name="version-information"></a>Informace o verzi  
 **Aplikace .NET pro Windows Store**  
  
 Podporováno v systému: Windows 8.1  
  
## <a name="see-also"></a>Viz také  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions`  
 [Postupy: Převádění mezi streamy rozhraní .NET Framework a streamy prostředí Windows Runtime](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
