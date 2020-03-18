---
title: Vyrovnávací paměti protokolu - gRPC pro vývojáře WCF
description: Úvod do drátového formátu Protocol Buffers používaného pro sítě gRPC.
ms.date: 09/09/2019
ms.openlocfilehash: 35319d299a8bc2866a87954b3e54bfda9314ffe8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147929"
---
# <a name="protocol-buffers"></a><span data-ttu-id="cba6d-103">Vyrovnávací paměti protokolu</span><span class="sxs-lookup"><span data-stu-id="cba6d-103">Protocol buffers</span></span>

<span data-ttu-id="cba6d-104">gRPC služby odesílat a přijímat data jako *protokol buffer (Protobuf) zprávy*, podobně jako datové smlouvy v Systému Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="cba6d-104">gRPC services send and receive data as *Protocol Buffer (Protobuf) messages*, similar to data contracts in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="cba6d-105">Protobuf je efektivní způsob serializace strukturovaných dat pro počítače ke čtení a zápisu, bez režie, které člověk čitelné formáty jako XML nebo JSON vzniknou.</span><span class="sxs-lookup"><span data-stu-id="cba6d-105">Protobuf is an efficient way of serializing structured data for machines to read and write, without the overhead that human-readable formats like XML or JSON incur.</span></span>

<span data-ttu-id="cba6d-106">Tato kapitola popisuje, jak Protobuf funguje a jak definovat vlastní zprávy Protobuf.</span><span class="sxs-lookup"><span data-stu-id="cba6d-106">This chapter covers how Protobuf works, and how to define your own Protobuf messages.</span></span>

## <a name="how-protobuf-works"></a><span data-ttu-id="cba6d-107">Jak přípravek Protobuf působí</span><span class="sxs-lookup"><span data-stu-id="cba6d-107">How Protobuf works</span></span>

<span data-ttu-id="cba6d-108">Většina technik serializace objektů .NET, včetně kontraktů dat WCF, pracuje pomocí reflexe k analýze struktury objektu za běhu.</span><span class="sxs-lookup"><span data-stu-id="cba6d-108">Most .NET object serialization techniques, including WCF's data contracts, work by using reflection to analyze the object structure at runtime.</span></span> <span data-ttu-id="cba6d-109">Naproti tomu většina knihoven Protobuf vyžaduje, abyste definovali strukturu předem pomocí vyhrazeného jazyka (*Jazyk vyrovnávací paměti protokolu*) v souboru. `.proto`</span><span class="sxs-lookup"><span data-stu-id="cba6d-109">By contrast, most Protobuf libraries require you to define the structure up front by using a dedicated language (*Protocol Buffer Language*) in a `.proto` file.</span></span> <span data-ttu-id="cba6d-110">Kompilátor pak používá tento soubor ke generování kódu pro některou z podporovaných platforem.</span><span class="sxs-lookup"><span data-stu-id="cba6d-110">A compiler then uses this file to generate code for any of the supported platforms.</span></span> <span data-ttu-id="cba6d-111">Mezi podporované platformy patří .NET, Java, C/C++, JavaScript a mnoho dalších.</span><span class="sxs-lookup"><span data-stu-id="cba6d-111">Supported platforms include .NET, Java, C/C++, JavaScript, and many more.</span></span>

<span data-ttu-id="cba6d-112">Kompilátor Protobuf `protoc`, je spravován společností Google, i když jsou k dispozici alternativní implementace.</span><span class="sxs-lookup"><span data-stu-id="cba6d-112">The Protobuf compiler, `protoc`, is maintained by Google, although alternative implementations are available.</span></span> <span data-ttu-id="cba6d-113">Generovaný kód je efektivní a optimalizovaný pro rychlou serializaci a deserializaci dat.</span><span class="sxs-lookup"><span data-stu-id="cba6d-113">The generated code is efficient and optimized for fast serialization and deserialization of data.</span></span>

<span data-ttu-id="cba6d-114">Formát drátu Protobuf je binární kódování.</span><span class="sxs-lookup"><span data-stu-id="cba6d-114">The Protobuf wire format is a binary encoding.</span></span> <span data-ttu-id="cba6d-115">Používá některé chytré triky, aby se minimalizoval počet bajtů používaných k reprezentaci zpráv.</span><span class="sxs-lookup"><span data-stu-id="cba6d-115">It uses some clever tricks to minimize the number of bytes used to represent messages.</span></span> <span data-ttu-id="cba6d-116">Znalost binárního formátu kódování není nutné používat Protobuf.</span><span class="sxs-lookup"><span data-stu-id="cba6d-116">Knowledge of the binary encoding format isn't necessary to use Protobuf.</span></span> <span data-ttu-id="cba6d-117">Ale pokud máte zájem, můžete se dozvědět více o tom na [webových stránkách protocol buffers](https://developers.google.com/protocol-buffers/docs/encoding).</span><span class="sxs-lookup"><span data-stu-id="cba6d-117">But if you're interested, you can learn more about it on [the Protocol Buffers website](https://developers.google.com/protocol-buffers/docs/encoding).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="cba6d-118">[Předchozí](why-grpc.md)
>[další](protobuf-messages.md)</span><span class="sxs-lookup"><span data-stu-id="cba6d-118">[Previous](why-grpc.md)
[Next](protobuf-messages.md)</span></span>
