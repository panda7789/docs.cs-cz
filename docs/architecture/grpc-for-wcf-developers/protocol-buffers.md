---
title: Vyrovnávací paměti protokolu – gRPC pro vývojáře WCF
description: Seznámení s formátem přenosu vyrovnávací paměti protokolu používaného pro gRPC sítě.
ms.date: 09/09/2019
ms.openlocfilehash: dbe8cb43475cfeec19051daf68452ef86269372f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967291"
---
# <a name="protocol-buffers"></a><span data-ttu-id="91417-103">Vyrovnávací paměti protokolu</span><span class="sxs-lookup"><span data-stu-id="91417-103">Protocol buffers</span></span>

<span data-ttu-id="91417-104">gRPC Services odesílají a přijímají zprávy o datech jako *vyrovnávací paměť protokolu (Protobuf)* , podobně jako kontrakty dat WCF.</span><span class="sxs-lookup"><span data-stu-id="91417-104">gRPC services send and receive data as *Protocol Buffer (Protobuf) messages*, similar to WCF's data contracts.</span></span> <span data-ttu-id="91417-105">Protobuf je efektivní způsob serializace strukturovaných dat pro počítače ke čtení a zápisu bez režie, kterou uživatelsky čitelné formáty, jako je například XML nebo JSON, neúčtují.</span><span class="sxs-lookup"><span data-stu-id="91417-105">Protobuf is an efficient way of serializing structured data for machines to read and write, without the overhead that human-readable formats like XML or JSON incur.</span></span>

<span data-ttu-id="91417-106">Tato kapitola popisuje, jak Protobuf funguje, a jak definovat vlastní zprávy Protobuf.</span><span class="sxs-lookup"><span data-stu-id="91417-106">This chapter covers how Protobuf works, and how to define your own Protobuf messages.</span></span>

## <a name="how-protobuf-works"></a><span data-ttu-id="91417-107">Jak funguje Protobuf</span><span class="sxs-lookup"><span data-stu-id="91417-107">How Protobuf works</span></span>

<span data-ttu-id="91417-108">Většina metod serializace objektů rozhraní .NET, včetně kontraktů dat WCF, funguje pomocí reflexe k analýze struktury objektů za běhu.</span><span class="sxs-lookup"><span data-stu-id="91417-108">Most .NET object serialization techniques, including WCF's data contracts, work by using reflection to analyze the object structure at run time.</span></span> <span data-ttu-id="91417-109">Naproti tomu většina Protobuf knihoven vyžaduje, abyste v souboru `.proto` definovali strukturu předem pomocí vyhrazeného jazyka (pro*vyrovnávací paměť protokolu*).</span><span class="sxs-lookup"><span data-stu-id="91417-109">By contrast, most Protobuf libraries require you to define the structure up front using a dedicated language (*Protocol Buffer Language*) in a `.proto` file.</span></span> <span data-ttu-id="91417-110">Tento soubor je poté používán kompilátorem k vygenerování kódu pro libovolnou z podporovaných platforem, včetně .NET, Java, C/C++, JavaScriptu a spousty dalších.</span><span class="sxs-lookup"><span data-stu-id="91417-110">This file is then used by a compiler to generate code for any of the supported platforms, including .NET, Java, C/C++, JavaScript, and many more.</span></span> <span data-ttu-id="91417-111">Kompilátor Protobuf, `protoc`, je udržován v Google, i když jsou k dispozici alternativní implementace.</span><span class="sxs-lookup"><span data-stu-id="91417-111">The Protobuf compiler, `protoc`, is maintained by Google, although alternative implementations are available.</span></span> <span data-ttu-id="91417-112">Generovaný kód je efektivní a optimalizovaný pro rychlou serializaci a deserializaci dat.</span><span class="sxs-lookup"><span data-stu-id="91417-112">The generated code is efficient and optimized for fast serialization and deserialization of data.</span></span>

<span data-ttu-id="91417-113">Samotný formát Protobuf kabelu je binární kódování, které používá některé chytřejší štychy k minimalizaci počtu bajtů používaných k reprezentování zpráv.</span><span class="sxs-lookup"><span data-stu-id="91417-113">The Protobuf wire format itself is a binary encoding, which uses some clever tricks to minimize the number of bytes used to represent messages.</span></span> <span data-ttu-id="91417-114">Znalost binárního formátu kódování není nutná k používání Protobuf, ale pokud vás zajímá, můžete o něm získat další informace na webu [vyrovnávací paměti protokolu](https://developers.google.com/protocol-buffers/docs/encoding).</span><span class="sxs-lookup"><span data-stu-id="91417-114">Knowledge of the binary encoding format isn't necessary to use Protobuf, but if you're interested you can learn more about it on [the Protocol Buffers web site](https://developers.google.com/protocol-buffers/docs/encoding).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="91417-115">[Předchozí](why-grpc.md)
>[Další](protobuf-messages.md)</span><span class="sxs-lookup"><span data-stu-id="91417-115">[Previous](why-grpc.md)
[Next](protobuf-messages.md)</span></span>
