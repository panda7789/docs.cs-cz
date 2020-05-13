---
title: Serializace – .NET
description: Tento článek obsahuje informace o technologiích serializace .NET, včetně binární serializace, XML a serializace SOAP a serializace JSON.
ms.date: 09/02/2019
helpviewer_keywords:
- JSON serialization
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: b3d76c14dc9180a5f19781122d1a42bcae603e76
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377245"
---
# <a name="serialization-in-net"></a><span data-ttu-id="c6f34-103">Serializace v .NET</span><span class="sxs-lookup"><span data-stu-id="c6f34-103">Serialization in .NET</span></span>

<span data-ttu-id="c6f34-104">Serializace je proces převodu stav objektu do tvaru, který může být zachována nebo přenosu.</span><span class="sxs-lookup"><span data-stu-id="c6f34-104">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="c6f34-105">Doplňkovým serializace je deserializace, která převádí na objekt datového proudu.</span><span class="sxs-lookup"><span data-stu-id="c6f34-105">The complement of serialization is deserialization, which converts a stream into an object.</span></span> <span data-ttu-id="c6f34-106">Tyto procesy společně umožňují ukládání a přenos dat.</span><span class="sxs-lookup"><span data-stu-id="c6f34-106">Together, these processes allow data to be stored and transferred.</span></span>  
  
<span data-ttu-id="c6f34-107">Rozhraní .NET nabízí tyto technologie serializace:</span><span class="sxs-lookup"><span data-stu-id="c6f34-107">.NET features the following serialization technologies:</span></span>  
  
- <span data-ttu-id="c6f34-108">[Binární serializace](binary-serialization.md) zachovává věrnost typu, což je užitečné pro zachování stavu objektu mezi různými voláními aplikace.</span><span class="sxs-lookup"><span data-stu-id="c6f34-108">[Binary serialization](binary-serialization.md) preserves type fidelity, which is useful for preserving the state of an object between different invocations of an application.</span></span> <span data-ttu-id="c6f34-109">Například můžete sdílet objekt mezi různými aplikacemi pomocí jeho serializace do schránky.</span><span class="sxs-lookup"><span data-stu-id="c6f34-109">For example, you can share an object between different applications by serializing it to the Clipboard.</span></span> <span data-ttu-id="c6f34-110">Může serializovat objekt do datového proudu, na disk do paměti, v síti a tak dále.</span><span class="sxs-lookup"><span data-stu-id="c6f34-110">You can serialize an object to a stream, to a disk, to memory, over the network, and so forth.</span></span> <span data-ttu-id="c6f34-111">Vzdálená komunikace používá serializace k předání objekty "hodnotou" z jedné domény počítače nebo aplikace do jiného.</span><span class="sxs-lookup"><span data-stu-id="c6f34-111">Remoting uses serialization to pass objects "by value" from one computer or application domain to another.</span></span>  
  
- <span data-ttu-id="c6f34-112">[Serializace XML a SOAP](xml-and-soap-serialization.md) serializovat pouze veřejné vlastnosti a pole a nezachovává věrnost typu.</span><span class="sxs-lookup"><span data-stu-id="c6f34-112">[XML and SOAP serialization](xml-and-soap-serialization.md) serializes only public properties and fields and does not preserve type fidelity.</span></span> <span data-ttu-id="c6f34-113">To je užitečné, pokud chcete zadat nebo spotřebovat data bez omezení aplikace, která používá data.</span><span class="sxs-lookup"><span data-stu-id="c6f34-113">This is useful when you want to provide or consume data without restricting the application that uses the data.</span></span> <span data-ttu-id="c6f34-114">Protože kód XML je otevřený standard, je to atraktivní volba pro sdílení dat v rámci webu.</span><span class="sxs-lookup"><span data-stu-id="c6f34-114">Because XML is an open standard, it is an attractive choice for sharing data across the Web.</span></span> <span data-ttu-id="c6f34-115">Protokol SOAP je rovněž otevřený standard, díky čemuž je atraktivní výběru.</span><span class="sxs-lookup"><span data-stu-id="c6f34-115">SOAP is likewise an open standard, which makes it an attractive choice.</span></span>  
  
- <span data-ttu-id="c6f34-116">[Serializace JSON](system-text-json-overview.md) pouze veřejné vlastnosti a nezachovává věrnost typu.</span><span class="sxs-lookup"><span data-stu-id="c6f34-116">[JSON serialization](system-text-json-overview.md) serializes only public properties and does not preserve type fidelity.</span></span> <span data-ttu-id="c6f34-117">JSON je otevřený standard, který je atraktivní volbou pro sdílení dat na celém webu.</span><span class="sxs-lookup"><span data-stu-id="c6f34-117">JSON is an open standard that is an attractive choice for sharing data across the web.</span></span>

## <a name="reference"></a><span data-ttu-id="c6f34-118">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="c6f34-118">Reference</span></span>

<xref:System.Runtime.Serialization>  
<span data-ttu-id="c6f34-119">Obsahuje třídy, které lze použít pro serializaci a deserializaci objektů.</span><span class="sxs-lookup"><span data-stu-id="c6f34-119">Contains classes that can be used for serializing and deserializing objects.</span></span>
  
<xref:System.Xml.Serialization>  
<span data-ttu-id="c6f34-120">Obsahuje třídy, které lze použít k serializaci objektů do formátu dokumentů XML nebo datových proudů.</span><span class="sxs-lookup"><span data-stu-id="c6f34-120">Contains classes that can be used to serialize objects into XML format documents or streams.</span></span>

<xref:System.Text.Json>  
<span data-ttu-id="c6f34-121">Obsahuje třídy, které lze použít k serializaci objektů do dokumentů formátu JSON nebo datových proudů.</span><span class="sxs-lookup"><span data-stu-id="c6f34-121">Contains classes that can be used to serialize objects into JSON format documents or streams.</span></span>
