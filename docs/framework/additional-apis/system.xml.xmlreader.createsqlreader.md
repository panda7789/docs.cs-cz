---
title: XmlReader. CreateSqlReader – metoda (System. XML)
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: c65ef7c073175488c11c5e912a44d46fd4319209
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215452"
---
# <a name="xmlreadercreatesqlreader-method"></a><span data-ttu-id="eb89e-102">XmlReader.CreateSqlReader – metoda</span><span class="sxs-lookup"><span data-stu-id="eb89e-102">XmlReader.CreateSqlReader Method</span></span>

<span data-ttu-id="eb89e-103">Vytvoří novou instanci <xref:System.Xml.XmlReader> pomocí zadaného datového proudu, nastavení a kontextové informace pro analýzu.</span><span class="sxs-lookup"><span data-stu-id="eb89e-103">Creates a new <xref:System.Xml.XmlReader> instance using the specified stream, settings, and context information for parsing.</span></span>

```csharp
internal static XmlReader CreateSqlReader(Stream input, 
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a><span data-ttu-id="eb89e-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb89e-104">Parameters</span></span>

- <span data-ttu-id="eb89e-105">`input` <xref:System.IO.Stream></span><span class="sxs-lookup"><span data-stu-id="eb89e-105">`input` <xref:System.IO.Stream></span></span>  
  <span data-ttu-id="eb89e-106">Datový proud, který obsahuje data XML.</span><span class="sxs-lookup"><span data-stu-id="eb89e-106">The stream that contains the XML data.</span></span>

- <span data-ttu-id="eb89e-107">`settings` <xref:System.Xml.XmlReaderSettings></span><span class="sxs-lookup"><span data-stu-id="eb89e-107">`settings` <xref:System.Xml.XmlReaderSettings></span></span>  
  <span data-ttu-id="eb89e-108">Nastavení pro novou instanci <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="eb89e-108">The settings for the new <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="eb89e-109">Tato hodnota může být `null`.</span><span class="sxs-lookup"><span data-stu-id="eb89e-109">This value can be `null`.</span></span>

- <span data-ttu-id="eb89e-110">`inputContext` <xref:System.Xml.XmlParserContext></span><span class="sxs-lookup"><span data-stu-id="eb89e-110">`inputContext` <xref:System.Xml.XmlParserContext></span></span>  
  <span data-ttu-id="eb89e-111">Kontextové informace vyžadované k analýze fragmentu XML.</span><span class="sxs-lookup"><span data-stu-id="eb89e-111">The context information required to parse the XML fragment.</span></span> <span data-ttu-id="eb89e-112">Tato hodnota může být `null`.</span><span class="sxs-lookup"><span data-stu-id="eb89e-112">This value can be `null`.</span></span>

## <a name="returns"></a><span data-ttu-id="eb89e-113">Vrací</span><span class="sxs-lookup"><span data-stu-id="eb89e-113">Returns</span></span>

<xref:System.Xml.XmlReader>  
<span data-ttu-id="eb89e-114">Objekt, který se používá ke čtení dat XML v datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="eb89e-114">An object that is used to read the XML data in the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="eb89e-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb89e-115">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="eb89e-116">Metoda `XmlReader.CreateSqlReader` je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="eb89e-116">The `XmlReader.CreateSqlReader` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="eb89e-117">Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="eb89e-117">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="eb89e-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb89e-118">Requirements</span></span>

<span data-ttu-id="eb89e-119">**Obor názvů:** <xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="eb89e-119">**Namespace:** <xref:System.Xml></span></span>

<span data-ttu-id="eb89e-120">**Sestavení:** System. XML. dll</span><span class="sxs-lookup"><span data-stu-id="eb89e-120">**Assembly:** System.Xml.dll</span></span>

<span data-ttu-id="eb89e-121">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="eb89e-121">**.NET Framework versions:** Available since 2.0.</span></span>
