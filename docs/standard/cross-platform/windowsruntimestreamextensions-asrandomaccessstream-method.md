---
title: "WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
api_name:
- System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream
api_location:
- System.Runtime.WindowsRuntime.dll
ms.assetid: dcc72283-caed-49ee-b45d-ccaf94e97129
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9057eabb7e3dfdfaa872fbcf2fe1180d0bbc7920
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a>WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) – metoda
[Podporované v rozhraní .NET Framework 4.5.1 a novějších verzích]  
  
 Převede zadaný datový proud na datový proud s náhodným přístupem.  
  
 **Namespace:**<xref:System.IO?displayProperty=nameWithType>  
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
  
 Typ:<xref:System.IO.Stream?displayProperty=nameWithType>  
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
