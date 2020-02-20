---
title: Vyrovnávací paměti protokolu – gRPC pro vývojáře WCF
description: Seznámení s formátem přenosu vyrovnávací paměti protokolu používaného pro gRPC sítě.
ms.date: 09/09/2019
ms.openlocfilehash: cc4ff272a9912d6f2dd8f8ddb1972c7369f980fe
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503452"
---
# <a name="protocol-buffers"></a><span data-ttu-id="1938f-103">Vyrovnávací paměti protokolu</span><span class="sxs-lookup"><span data-stu-id="1938f-103">Protocol buffers</span></span>

<span data-ttu-id="1938f-104">gRPC Services odesílají a přijímají zprávy o datech jako *vyrovnávací paměť protokolu (Protobuf)* , podobně jako kontrakty dat v Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1938f-104">gRPC services send and receive data as *Protocol Buffer (Protobuf) messages*, similar to data contracts in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="1938f-105">Protobuf je efektivní způsob serializace strukturovaných dat pro počítače ke čtení a zápisu bez režie, kterou uživatelsky čitelné formáty, jako je například XML nebo JSON, neúčtují.</span><span class="sxs-lookup"><span data-stu-id="1938f-105">Protobuf is an efficient way of serializing structured data for machines to read and write, without the overhead that human-readable formats like XML or JSON incur.</span></span>

<span data-ttu-id="1938f-106">Tato kapitola popisuje, jak Protobuf funguje, a jak definovat vlastní zprávy Protobuf.</span><span class="sxs-lookup"><span data-stu-id="1938f-106">This chapter covers how Protobuf works, and how to define your own Protobuf messages.</span></span>

## <a name="how-protobuf-works"></a><span data-ttu-id="1938f-107">Jak funguje Protobuf</span><span class="sxs-lookup"><span data-stu-id="1938f-107">How Protobuf works</span></span>

<span data-ttu-id="1938f-108">Většina metod serializace objektů rozhraní .NET, včetně kontraktů dat WCF, funguje pomocí reflexe k analýze struktury objektů za běhu.</span><span class="sxs-lookup"><span data-stu-id="1938f-108">Most .NET object serialization techniques, including WCF's data contracts, work by using reflection to analyze the object structure at runtime.</span></span> <span data-ttu-id="1938f-109">Naproti tomu většina Protobuf knihoven vyžaduje, abyste definovali strukturu předem pomocí vyhrazeného jazyka (*jazyk vyrovnávací paměti protokolu*) v souboru `.proto`.</span><span class="sxs-lookup"><span data-stu-id="1938f-109">By contrast, most Protobuf libraries require you to define the structure up front by using a dedicated language (*Protocol Buffer Language*) in a `.proto` file.</span></span> <span data-ttu-id="1938f-110">Kompilátor potom pomocí tohoto souboru vygeneruje kód pro libovolnou z podporovaných platforem.</span><span class="sxs-lookup"><span data-stu-id="1938f-110">A compiler then uses this file to generate code for any of the supported platforms.</span></span> <span data-ttu-id="1938f-111">Mezi podporované platformy patří .NET, Java, CC++/, JavaScript a spousta dalších.</span><span class="sxs-lookup"><span data-stu-id="1938f-111">Supported platforms include .NET, Java, C/C++, JavaScript, and many more.</span></span> 

<span data-ttu-id="1938f-112">Kompilátor Protobuf, `protoc`, je udržován v Google, i když jsou k dispozici alternativní implementace.</span><span class="sxs-lookup"><span data-stu-id="1938f-112">The Protobuf compiler, `protoc`, is maintained by Google, although alternative implementations are available.</span></span> <span data-ttu-id="1938f-113">Generovaný kód je efektivní a optimalizovaný pro rychlou serializaci a deserializaci dat.</span><span class="sxs-lookup"><span data-stu-id="1938f-113">The generated code is efficient and optimized for fast serialization and deserialization of data.</span></span>

<span data-ttu-id="1938f-114">Formát Protobuf drátu je binární kódování.</span><span class="sxs-lookup"><span data-stu-id="1938f-114">The Protobuf wire format is a binary encoding.</span></span> <span data-ttu-id="1938f-115">K minimalizaci počtu bajtů použitých k reprezentování zpráv používá některé chytřejší triky.</span><span class="sxs-lookup"><span data-stu-id="1938f-115">It uses some clever tricks to minimize the number of bytes used to represent messages.</span></span> <span data-ttu-id="1938f-116">Znalost formátu binárního kódování není nutná k použití Protobuf.</span><span class="sxs-lookup"><span data-stu-id="1938f-116">Knowledge of the binary encoding format isn't necessary to use Protobuf.</span></span> <span data-ttu-id="1938f-117">Pokud vás ale zajímá, můžete o něm získat další informace na [webu vyrovnávací paměti protokolu](https://developers.google.com/protocol-buffers/docs/encoding).</span><span class="sxs-lookup"><span data-stu-id="1938f-117">But if you're interested, you can learn more about it on [the Protocol Buffers website](https://developers.google.com/protocol-buffers/docs/encoding).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1938f-118">[Předchozí](why-grpc.md)
>[Další](protobuf-messages.md)</span><span class="sxs-lookup"><span data-stu-id="1938f-118">[Previous](why-grpc.md)
[Next](protobuf-messages.md)</span></span>
