---
title: Serializace – .NET
ms.date: 09/02/2019
helpviewer_keywords:
- JSON serialization
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: e6db24326c79ab6509b253c45c27f87a2aacd73c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053351"
---
# <a name="serialization-in-net"></a><span data-ttu-id="11684-102">Serializace v .NET</span><span class="sxs-lookup"><span data-stu-id="11684-102">Serialization in .NET</span></span>

<span data-ttu-id="11684-103">Serializace je proces převodu stav objektu do tvaru, který může být zachována nebo přenosu.</span><span class="sxs-lookup"><span data-stu-id="11684-103">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="11684-104">Doplňkovým serializace je deserializace, která převádí na objekt datového proudu.</span><span class="sxs-lookup"><span data-stu-id="11684-104">The complement of serialization is deserialization, which converts a stream into an object.</span></span> <span data-ttu-id="11684-105">Tyto procesy společně umožňují ukládání a přenos dat.</span><span class="sxs-lookup"><span data-stu-id="11684-105">Together, these processes allow data to be stored and transferred.</span></span>  
  
<span data-ttu-id="11684-106">Rozhraní .NET nabízí tyto technologie serializace:</span><span class="sxs-lookup"><span data-stu-id="11684-106">.NET features the following serialization technologies:</span></span>  
  
- <span data-ttu-id="11684-107">[Binární serializace](binary-serialization.md) zachovává věrnost typu, což je užitečné pro zachování stavu objektu mezi různými voláními aplikace.</span><span class="sxs-lookup"><span data-stu-id="11684-107">[Binary serialization](binary-serialization.md) preserves type fidelity, which is useful for preserving the state of an object between different invocations of an application.</span></span> <span data-ttu-id="11684-108">Například můžete sdílet objekt mezi různými aplikacemi pomocí jeho serializace do schránky.</span><span class="sxs-lookup"><span data-stu-id="11684-108">For example, you can share an object between different applications by serializing it to the Clipboard.</span></span> <span data-ttu-id="11684-109">Může serializovat objekt do datového proudu, na disk do paměti, v síti a tak dále.</span><span class="sxs-lookup"><span data-stu-id="11684-109">You can serialize an object to a stream, to a disk, to memory, over the network, and so forth.</span></span> <span data-ttu-id="11684-110">Vzdálená komunikace používá serializace k předání objekty "hodnotou" z jedné domény počítače nebo aplikace do jiného.</span><span class="sxs-lookup"><span data-stu-id="11684-110">Remoting uses serialization to pass objects "by value" from one computer or application domain to another.</span></span>  
  
- <span data-ttu-id="11684-111">[Serializace XML a SOAP](xml-and-soap-serialization.md) serializovat pouze veřejné vlastnosti a pole a nezachovává věrnost typu.</span><span class="sxs-lookup"><span data-stu-id="11684-111">[XML and SOAP serialization](xml-and-soap-serialization.md) serializes only public properties and fields and does not preserve type fidelity.</span></span> <span data-ttu-id="11684-112">To je užitečné, pokud chcete zadat nebo spotřebovat data bez omezení aplikace, která používá data.</span><span class="sxs-lookup"><span data-stu-id="11684-112">This is useful when you want to provide or consume data without restricting the application that uses the data.</span></span> <span data-ttu-id="11684-113">Protože kód XML je otevřený standard, je to atraktivní volba pro sdílení dat v rámci webu.</span><span class="sxs-lookup"><span data-stu-id="11684-113">Because XML is an open standard, it is an attractive choice for sharing data across the Web.</span></span> <span data-ttu-id="11684-114">Protokol SOAP je rovněž otevřený standard, díky čemuž je atraktivní výběru.</span><span class="sxs-lookup"><span data-stu-id="11684-114">SOAP is likewise an open standard, which makes it an attractive choice.</span></span>  
  
- <span data-ttu-id="11684-115">[Serializace JSON](system-text-json-overview.md) pouze veřejné vlastnosti a nezachovává věrnost typu.</span><span class="sxs-lookup"><span data-stu-id="11684-115">[JSON serialization](system-text-json-overview.md) serializes only public properties and does not preserve type fidelity.</span></span> <span data-ttu-id="11684-116">JSON je otevřený standard, který je atraktivní volbou pro sdílení dat na celém webu.</span><span class="sxs-lookup"><span data-stu-id="11684-116">JSON is an open standard that is an attractive choice for sharing data across the web.</span></span>

## <a name="reference"></a><span data-ttu-id="11684-117">Reference</span><span class="sxs-lookup"><span data-stu-id="11684-117">Reference</span></span>

<xref:System.Runtime.Serialization>  
<span data-ttu-id="11684-118">Obsahuje třídy, které lze použít pro serializaci a deserializaci objektů.</span><span class="sxs-lookup"><span data-stu-id="11684-118">Contains classes that can be used for serializing and deserializing objects.</span></span>
  
<xref:System.Xml.Serialization>  
<span data-ttu-id="11684-119">Obsahuje třídy, které lze použít k serializaci objektů do formátu dokumentů XML nebo datových proudů.</span><span class="sxs-lookup"><span data-stu-id="11684-119">Contains classes that can be used to serialize objects into XML format documents or streams.</span></span>

<xref:System.Text.Json>  
<span data-ttu-id="11684-120">Obsahuje třídy, které lze použít k serializaci objektů do dokumentů formátu JSON nebo datových proudů.</span><span class="sxs-lookup"><span data-stu-id="11684-120">Contains classes that can be used to serialize objects into JSON format documents or streams.</span></span>
