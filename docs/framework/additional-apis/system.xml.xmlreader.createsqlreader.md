---
title: Metoda XmlReader.CreateSqlReader (System.Xml)
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: 7bd2ef5158516acede47f73f9937d06159bc16c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155736"
---
# <a name="xmlreadercreatesqlreader-method"></a><span data-ttu-id="664a9-102">XmlReader.CreateSqlReader – metoda</span><span class="sxs-lookup"><span data-stu-id="664a9-102">XmlReader.CreateSqlReader Method</span></span>

<span data-ttu-id="664a9-103">Vytvoří novou <xref:System.Xml.XmlReader> instanci pomocí zadaného datového proudu, nastavení a kontextových informací pro analýzu.</span><span class="sxs-lookup"><span data-stu-id="664a9-103">Creates a new <xref:System.Xml.XmlReader> instance using the specified stream, settings, and context information for parsing.</span></span>

```csharp
internal static XmlReader CreateSqlReader(Stream input,
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a><span data-ttu-id="664a9-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="664a9-104">Parameters</span></span>

- <span data-ttu-id="664a9-105">`input` <xref:System.IO.Stream></span><span class="sxs-lookup"><span data-stu-id="664a9-105">`input` <xref:System.IO.Stream></span></span>  
  <span data-ttu-id="664a9-106">Datový proud, který obsahuje data XML.</span><span class="sxs-lookup"><span data-stu-id="664a9-106">The stream that contains the XML data.</span></span>

- <span data-ttu-id="664a9-107">`settings` <xref:System.Xml.XmlReaderSettings></span><span class="sxs-lookup"><span data-stu-id="664a9-107">`settings` <xref:System.Xml.XmlReaderSettings></span></span>  
  <span data-ttu-id="664a9-108">Nastavení pro novou <xref:System.Xml.XmlReader> instanci.</span><span class="sxs-lookup"><span data-stu-id="664a9-108">The settings for the new <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="664a9-109">Tato hodnota `null`může být .</span><span class="sxs-lookup"><span data-stu-id="664a9-109">This value can be `null`.</span></span>

- <span data-ttu-id="664a9-110">`inputContext` <xref:System.Xml.XmlParserContext></span><span class="sxs-lookup"><span data-stu-id="664a9-110">`inputContext` <xref:System.Xml.XmlParserContext></span></span>  
  <span data-ttu-id="664a9-111">Kontextové informace potřebné k analýzě fragmentu XML.</span><span class="sxs-lookup"><span data-stu-id="664a9-111">The context information required to parse the XML fragment.</span></span> <span data-ttu-id="664a9-112">Tato hodnota `null`může být .</span><span class="sxs-lookup"><span data-stu-id="664a9-112">This value can be `null`.</span></span>

## <a name="returns"></a><span data-ttu-id="664a9-113">Vrací</span><span class="sxs-lookup"><span data-stu-id="664a9-113">Returns</span></span>

<xref:System.Xml.XmlReader>  
<span data-ttu-id="664a9-114">Objekt, který se používá ke čtení dat XML v datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="664a9-114">An object that is used to read the XML data in the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="664a9-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="664a9-115">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="664a9-116">Metoda `XmlReader.CreateSqlReader` je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="664a9-116">The `XmlReader.CreateSqlReader` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="664a9-117">Společnost Microsoft nepodporuje použití této metody v produkční aplikaci za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="664a9-117">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="664a9-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="664a9-118">Requirements</span></span>

<span data-ttu-id="664a9-119">**Obor názvů:**<xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="664a9-119">**Namespace:** <xref:System.Xml></span></span>

<span data-ttu-id="664a9-120">**Sestava:** Soubor System.Xml.dll</span><span class="sxs-lookup"><span data-stu-id="664a9-120">**Assembly:** System.Xml.dll</span></span>

<span data-ttu-id="664a9-121">**Verze rozhraní .NET Framework:** K dispozici od 2.0.</span><span class="sxs-lookup"><span data-stu-id="664a9-121">**.NET Framework versions:** Available since 2.0.</span></span>
