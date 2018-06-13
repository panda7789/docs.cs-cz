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
ms.locfileid: "32768512"
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a><span data-ttu-id="e9e66-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) – metoda</span><span class="sxs-lookup"><span data-stu-id="e9e66-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Method</span></span>
<span data-ttu-id="e9e66-103">[Podporované v rozhraní .NET Framework 4.5.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="e9e66-103">[Supported in the .NET Framework 4.5.1 and later versions]</span></span>  
  
 <span data-ttu-id="e9e66-104">Převede zadaný datový proud na datový proud s náhodným přístupem.</span><span class="sxs-lookup"><span data-stu-id="e9e66-104">Converts the specified stream to a random access stream.</span></span>  
  
 <span data-ttu-id="e9e66-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e9e66-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType></span></span>  
 <span data-ttu-id="e9e66-106">**Sestavení:** System.Runtime.WindowsRuntime (v System.Runtime.WindowsRuntime.dll)</span><span class="sxs-lookup"><span data-stu-id="e9e66-106">**Assembly:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9e66-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9e66-107">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="e9e66-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9e66-108">Parameters</span></span>  
 `stream`  
  
 <span data-ttu-id="e9e66-109">Typ: <xref:System.IO.Stream?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e9e66-109">Type: <xref:System.IO.Stream?displayProperty=nameWithType></span></span>  
<span data-ttu-id="e9e66-110">Datový proud, který chcete převést.</span><span class="sxs-lookup"><span data-stu-id="e9e66-110">The stream to convert.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9e66-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e9e66-111">Return Value</span></span>  
 <span data-ttu-id="e9e66-112">Typ: [Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)</span><span class="sxs-lookup"><span data-stu-id="e9e66-112">Type: [Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)</span></span>  
<span data-ttu-id="e9e66-113">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] náhodný přístup datový proud, který představuje převedenou datového proudu.</span><span class="sxs-lookup"><span data-stu-id="e9e66-113">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] random access stream, which represents the converted stream.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="e9e66-114">Výjimky</span><span class="sxs-lookup"><span data-stu-id="e9e66-114">Exceptions</span></span>  
  
|<span data-ttu-id="e9e66-115">Výjimka</span><span class="sxs-lookup"><span data-stu-id="e9e66-115">Exception</span></span>|<span data-ttu-id="e9e66-116">Podmínka</span><span class="sxs-lookup"><span data-stu-id="e9e66-116">Condition</span></span>|  
|---------------|---------------|  
|<xref:System.NotSupportedException>|<span data-ttu-id="e9e66-117">Datový proud, který chcete převést, nepodporuje vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="e9e66-117">The stream to convert does not support seeking.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9e66-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9e66-118">Remarks</span></span>  
 <span data-ttu-id="e9e66-119">Tato metoda rozšíření je k dispozici pouze v případě, že vyvíjíte aplikace pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="e9e66-119">This extension method is available only when you develop Windows Store apps.</span></span> <span data-ttu-id="e9e66-120">Tato metoda poskytuje pohodlný způsob práce s datovými proudy v aplikacích pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="e9e66-120">This method provides a convenient way of working with streams in Windows Store apps.</span></span> <span data-ttu-id="e9e66-121">Datový proud rozhraní .NET Framework, který chcete převést musí podporovat hledání pozice.</span><span class="sxs-lookup"><span data-stu-id="e9e66-121">The .NET Framework stream you want to convert must support seeking.</span></span> <span data-ttu-id="e9e66-122">Další informace najdete v tématu <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="e9e66-122">For more information, see the <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e9e66-123">Toto rozhraní API je podporována v rozhraní .NET Framework 4.5.1 a novějších verzích, ale není v verze 4.5.</span><span class="sxs-lookup"><span data-stu-id="e9e66-123">This API is supported in the .NET Framework 4.5.1 and later versions, but not in version 4.5.</span></span>  
  
## <a name="version-information"></a><span data-ttu-id="e9e66-124">Informace o verzi</span><span class="sxs-lookup"><span data-stu-id="e9e66-124">Version Information</span></span>  
 <span data-ttu-id="e9e66-125">**Aplikace .NET pro Windows Store**</span><span class="sxs-lookup"><span data-stu-id="e9e66-125">**.NET for Windows Store apps**</span></span>  
  
 <span data-ttu-id="e9e66-126">Podporováno v systému: Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="e9e66-126">Supported in: Windows 8.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9e66-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9e66-127">See Also</span></span>  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions`  
 [<span data-ttu-id="e9e66-128">Postupy: Převádění mezi streamy rozhraní .NET Framework a streamy prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="e9e66-128">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
