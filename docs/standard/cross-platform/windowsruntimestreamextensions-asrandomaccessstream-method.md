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
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/06/2019
ms.locfileid: "55758791"
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a><span data-ttu-id="98bc2-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) – metoda</span><span class="sxs-lookup"><span data-stu-id="98bc2-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Method</span></span>

<span data-ttu-id="98bc2-103">[Podporované v rozhraní .NET Framework 4.5.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="98bc2-103">[Supported in the .NET Framework 4.5.1 and later versions]</span></span>

<span data-ttu-id="98bc2-104">Převede zadaný datový proud na datový proud s náhodným přístupem.</span><span class="sxs-lookup"><span data-stu-id="98bc2-104">Converts the specified stream to a random access stream.</span></span>

<span data-ttu-id="98bc2-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType>
**Sestavení:** System.Runtime.WindowsRuntime (v souboru System.Runtime.WindowsRuntime.dll)</span><span class="sxs-lookup"><span data-stu-id="98bc2-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType>
**Assembly:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)</span></span>

## <a name="syntax"></a><span data-ttu-id="98bc2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98bc2-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="98bc2-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="98bc2-107">Parameters</span></span>

`stream`

<span data-ttu-id="98bc2-108">Typ: <xref:System.IO.Stream?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="98bc2-108">Type: <xref:System.IO.Stream?displayProperty=nameWithType></span></span>  
<span data-ttu-id="98bc2-109">Datový proud, který chcete převést.</span><span class="sxs-lookup"><span data-stu-id="98bc2-109">The stream to convert.</span></span>

## <a name="return-value"></a><span data-ttu-id="98bc2-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="98bc2-110">Return Value</span></span>

<span data-ttu-id="98bc2-111">Typ: <xref:Windows.Storage.Streams.RandomAccessStream></span><span class="sxs-lookup"><span data-stu-id="98bc2-111">Type: <xref:Windows.Storage.Streams.RandomAccessStream></span></span>  
<span data-ttu-id="98bc2-112">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] stream náhodný přístup, který představuje převedený datový proud.</span><span class="sxs-lookup"><span data-stu-id="98bc2-112">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] random access stream, which represents the converted stream.</span></span>

## <a name="exceptions"></a><span data-ttu-id="98bc2-113">Výjimky</span><span class="sxs-lookup"><span data-stu-id="98bc2-113">Exceptions</span></span>

|<span data-ttu-id="98bc2-114">Výjimka</span><span class="sxs-lookup"><span data-stu-id="98bc2-114">Exception</span></span>|<span data-ttu-id="98bc2-115">Podmínka</span><span class="sxs-lookup"><span data-stu-id="98bc2-115">Condition</span></span>|
|---------------|---------------|
|<xref:System.NotSupportedException>|<span data-ttu-id="98bc2-116">Datový proud, který chcete převést, nepodporuje vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="98bc2-116">The stream to convert does not support seeking.</span></span>|

## <a name="remarks"></a><span data-ttu-id="98bc2-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="98bc2-117">Remarks</span></span>

<span data-ttu-id="98bc2-118">Tato metoda rozšíření je k dispozici pouze v případě, že vyvíjíte aplikace pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="98bc2-118">This extension method is available only when you develop Windows Store apps.</span></span> <span data-ttu-id="98bc2-119">Tato metoda poskytuje pohodlný způsob práce s datovými proudy v aplikacích pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="98bc2-119">This method provides a convenient way of working with streams in Windows Store apps.</span></span> <span data-ttu-id="98bc2-120">Datový proud rozhraní .NET Framework, kterou chcete převést, musí podporovat vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="98bc2-120">The .NET Framework stream you want to convert must support seeking.</span></span> <span data-ttu-id="98bc2-121">Další informace najdete v tématu <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="98bc2-121">For more information, see the <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="98bc2-122">Toto rozhraní API je podporováno v rozhraní .NET Framework 4.5.1 a novější verze, ale ne ve verzi 4.5.</span><span class="sxs-lookup"><span data-stu-id="98bc2-122">This API is supported in the .NET Framework 4.5.1 and later versions, but not in version 4.5.</span></span>

## <a name="version-information"></a><span data-ttu-id="98bc2-123">Informace o verzi</span><span class="sxs-lookup"><span data-stu-id="98bc2-123">Version Information</span></span>

<span data-ttu-id="98bc2-124">**.NET pro aplikace Windows Store**</span><span class="sxs-lookup"><span data-stu-id="98bc2-124">**.NET for Windows Store apps**</span></span>

<span data-ttu-id="98bc2-125">Podporované v: Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="98bc2-125">Supported in: Windows 8.1</span></span>

## <a name="see-also"></a><span data-ttu-id="98bc2-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98bc2-126">See also</span></span>

- [<span data-ttu-id="98bc2-127">Postupy: Převod mezi streamy rozhraní .NET Framework a datovými proudy Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="98bc2-127">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
