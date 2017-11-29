---
title: "Binární serializace"
ms.date: 08/11/2017
ms.prod: .net
ms.topic: article
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
caps.latest.revision: "5"
author: ViktorHofer
ms.author: mairaw
ms.openlocfilehash: 74ee4e21934c1e4f3fd008664b1315429dc47b37
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="binary-serialization"></a><span data-ttu-id="020ba-102">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="020ba-102">Binary serialization</span></span>

<span data-ttu-id="020ba-103">Serializace může být definován jako proces ukládání stavu objektu do úložiště média.</span><span class="sxs-lookup"><span data-stu-id="020ba-103">Serialization can be defined as the process of storing the state of an object to a storage medium.</span></span> <span data-ttu-id="020ba-104">Během tohoto procesu se veřejné a soukromé pole objektu a název třídy, včetně sestavení obsahující dané třídy, jsou převedeny do datového proudu bajtů, které jsou následně zapsána do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="020ba-104">During this process, the public and private fields of the object and the name of the class, including the assembly containing the class, are converted to a stream of bytes, which is then written to a data stream.</span></span> <span data-ttu-id="020ba-105">Při objektu je následně deserializovat, je vytvořena přesné klon původní objekt.</span><span class="sxs-lookup"><span data-stu-id="020ba-105">When the object is subsequently deserialized, an exact clone of the original object is created.</span></span>

<span data-ttu-id="020ba-106">Při provádění mechanismus serializace v prostředí objektově orientované, je třeba vytvořit počet kompromisy mezi snadnost použití a flexibilitu.</span><span class="sxs-lookup"><span data-stu-id="020ba-106">When implementing a serialization mechanism in an object-oriented environment, you have to make a number of tradeoffs between ease of use and flexibility.</span></span> <span data-ttu-id="020ba-107">Proces můžete automatizované do značné míry, za předpokladu, že budete mít dostatečné kontrolu nad procesem.</span><span class="sxs-lookup"><span data-stu-id="020ba-107">The process can be automated to a large extent, provided you are given sufficient control over the process.</span></span> <span data-ttu-id="020ba-108">Například může nastat situace, kde jednoduché binární serializace není dostatečné, nebo mohou existovat konkrétní důvod, proč se rozhodnout, která pole v třídě muset být serializován.</span><span class="sxs-lookup"><span data-stu-id="020ba-108">For example, situations may arise where simple binary serialization is not sufficient, or there might be a specific reason to decide which fields in a class need to be serialized.</span></span> <span data-ttu-id="020ba-109">Následující části vysvětlují mechanismu serializace robustní součástí rozhraní .NET a označte několik důležitých funkcí, které vám umožní přizpůsobit proces podle svých potřeb.</span><span class="sxs-lookup"><span data-stu-id="020ba-109">The following sections examine the robust serialization mechanism provided with .NET and highlight a number of important features that allow you to customize the process to meet your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="020ba-110">Stav UTF-8 nebo UTF-7 objekt není zachováváno, je-li objekt je serializaci a deserializaci pomocí různých verzí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="020ba-110">The state of a UTF-8 or UTF-7 encoded object is not preserved if the object is serialized and deserialized using different .NET Framework versions.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="020ba-111">Povaha binární serializace umožňuje úpravy soukromé členy uvnitř objekt a proto změny stavu je, jsou doporučené ostatní platformy serializace jako JSON.NET, které fungují na povrchu veřejné rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="020ba-111">As the nature of binary serialization allows the modification of private members inside an object and therefore changing the state of it, other serialization frameworks like JSON.NET which operate on the public API surface are recommended.</span></span>

## <a name="binary-serialization-in-net-core"></a><span data-ttu-id="020ba-112">Binární serializace v .NET Core</span><span class="sxs-lookup"><span data-stu-id="020ba-112">Binary serialization in .NET Core</span></span>

<span data-ttu-id="020ba-113">.NET core podporuje binární serializace s podmnožinu typů.</span><span class="sxs-lookup"><span data-stu-id="020ba-113">.NET Core supports binary serialization with a subset of types.</span></span> <span data-ttu-id="020ba-114">Zobrazí se seznam podporovaných typů v [Serializovatelné typy části](#serializable-types).</span><span class="sxs-lookup"><span data-stu-id="020ba-114">You can see the list of supported types in the [Serializable types section](#serializable-types).</span></span> <span data-ttu-id="020ba-115">Definovanou sadu typy jsou musí být serializovatelný mezi rozhraní .NET Framework 4.5.1 a novější verze rozhraní .NET Core 2.0 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="020ba-115">The defined set of types are guaranteed to be serializable between .NET Framework 4.5.1 and later versions and .NET Core 2.0 and later versions.</span></span> <span data-ttu-id="020ba-116">Jiné implementace rozhraní .NET, jako je například Mono, nejsou oficiálně podporované, ale také musí být práce.</span><span class="sxs-lookup"><span data-stu-id="020ba-116">Other .NET implementations, such as Mono, aren't officially supported but should also be working.</span></span>

### <a name="serializable-types"></a><span data-ttu-id="020ba-117">Serializovatelné typy</span><span class="sxs-lookup"><span data-stu-id="020ba-117">Serializable types</span></span>

- <xref:System.AggregateException?displayProperty=nameWithType>   
- <xref:System.Array?displayProperty=nameWithType>   
- <xref:System.ArraySegment%601?displayProperty=nameWithType>   
- <xref:System.Attribute?displayProperty=nameWithType>   
- <xref:System.Boolean?displayProperty=nameWithType>   
- <xref:System.Byte?displayProperty=nameWithType>   
- <xref:System.Char?displayProperty=nameWithType>   
- <xref:System.Collections.ArrayList?displayProperty=nameWithType>   
- <xref:System.Collections.BitArray?displayProperty=nameWithType>   
- <xref:System.Collections.Comparer?displayProperty=nameWithType>   
- <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType>   
- <xref:System.Collections.Hashtable?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.Queue?displayProperty=nameWithType>   
- <xref:System.Collections.SortedList?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Stack?displayProperty=nameWithType>   
- <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType>   
- <span data-ttu-id="020ba-118"><xref:System.DBNull?displayProperty=nameWithType>(k dispozici v .NET Core bodu 2.0.2 a novější)</span><span class="sxs-lookup"><span data-stu-id="020ba-118"><xref:System.DBNull?displayProperty=nameWithType> (available in .NET Core 2.0.2 and later versions)</span></span>   
- <xref:System.Data.DataSet?displayProperty=nameWithType>   
- <xref:System.Data.DataTable?displayProperty=nameWithType>   
- <xref:System.Data.PropertyCollection?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType>   
- <xref:System.DateTime?displayProperty=nameWithType>   
- <xref:System.DateTimeOffset?displayProperty=nameWithType>   
- <xref:System.Decimal?displayProperty=nameWithType>   
- <xref:System.Double?displayProperty=nameWithType>   
- <xref:System.Drawing.Color?displayProperty=nameWithType>   
- <xref:System.Drawing.Point?displayProperty=nameWithType>   
- <xref:System.Drawing.PointF?displayProperty=nameWithType>   
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>   
- <xref:System.Drawing.RectangleF?displayProperty=nameWithType>   
- <xref:System.Drawing.Size?displayProperty=nameWithType>   
- <xref:System.Drawing.SizeF?displayProperty=nameWithType>   
- <xref:System.Enum?displayProperty=nameWithType>   
- <xref:System.Exception?displayProperty=nameWithType>   
- <xref:System.Globalization.CompareInfo?displayProperty=nameWithType>   
- <xref:System.Globalization.SortVersion?displayProperty=nameWithType>   
- <xref:System.Guid?displayProperty=nameWithType>   
- <xref:System.Int16?displayProperty=nameWithType>   
- <xref:System.Int32?displayProperty=nameWithType>   
- <xref:System.Int64?displayProperty=nameWithType>   
- <xref:System.IntPtr?displayProperty=nameWithType>   
- <xref:System.Net.Cookie?displayProperty=nameWithType>   
- <xref:System.Net.CookieCollection?displayProperty=nameWithType>   
- <xref:System.Net.CookieContainer?displayProperty=nameWithType>   
- <xref:System.Nullable%601?displayProperty=nameWithType>   
- <xref:System.Numerics.BigInteger?displayProperty=nameWithType>   
- <xref:System.Numerics.Complex?displayProperty=nameWithType>   
- <xref:System.Object?displayProperty=nameWithType>   
- <xref:System.SByte?displayProperty=nameWithType>   
- <xref:System.Single?displayProperty=nameWithType>   
- <xref:System.String?displayProperty=nameWithType>   
- <xref:System.StringComparer?displayProperty=nameWithType>   
- <xref:System.Text.StringBuilder?displayProperty=nameWithType>   
- <xref:System.TimeSpan?displayProperty=nameWithType>   
- <xref:System.TimeZoneInfo?displayProperty=nameWithType>   
- <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType>   
- <xref:System.Tuple?displayProperty=nameWithType>   
- <xref:System.UInt16?displayProperty=nameWithType>   
- <xref:System.UInt32?displayProperty=nameWithType>   
- <xref:System.UInt64?displayProperty=nameWithType>   
- <xref:System.UIntPtr?displayProperty=nameWithType>   
- <xref:System.Uri?displayProperty=nameWithType>   
- <span data-ttu-id="020ba-119"><xref:System.ValueTuple?displayProperty=nameWithType>(není serializovatelný v rozhraní .NET Framework 4.7 a starší verze)</span><span class="sxs-lookup"><span data-stu-id="020ba-119"><xref:System.ValueTuple?displayProperty=nameWithType> (not serializable in .NET Framework 4.7 and earlier versions)</span></span>  
- <xref:System.ValueType?displayProperty=nameWithType>   
- <xref:System.Version?displayProperty=nameWithType>   
- <xref:System.WeakReference?displayProperty=nameWithType>   
- <xref:System.WeakReference%601?displayProperty=nameWithType>   

## <a name="in-this-section"></a><span data-ttu-id="020ba-120">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="020ba-120">In this section</span></span>

 [<span data-ttu-id="020ba-121">Koncepty serializace</span><span class="sxs-lookup"><span data-stu-id="020ba-121">Serialization Concepts</span></span>](../../../docs/standard/serialization/serialization-concepts.md)  
 <span data-ttu-id="020ba-122">Popisuje dva scénáře, kde je serializace užitečná: Pokud zachovává data do úložiště a při předávání objektů mezi doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="020ba-122">Discusses two scenarios where serialization is useful: when persisting data to storage and when passing objects across application domains.</span></span>  
  
 [<span data-ttu-id="020ba-123">Základní serializace</span><span class="sxs-lookup"><span data-stu-id="020ba-123">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)  
 <span data-ttu-id="020ba-124">Popisuje, jak používat binárního souboru a SOAP formátovacích modulů k serializaci objektů.</span><span class="sxs-lookup"><span data-stu-id="020ba-124">Describes how to use the binary and SOAP formatters to serialize objects.</span></span>  
  
 [<span data-ttu-id="020ba-125">Selektivní serializace</span><span class="sxs-lookup"><span data-stu-id="020ba-125">Selective Serialization</span></span>](../../../docs/standard/serialization/selective-serialization.md)  
 <span data-ttu-id="020ba-126">Popisuje, jak zabránit serializována některé členy třídy.</span><span class="sxs-lookup"><span data-stu-id="020ba-126">Describes how to prevent some members of a class from being serialized.</span></span>  
  
 [<span data-ttu-id="020ba-127">Vlastní serializace</span><span class="sxs-lookup"><span data-stu-id="020ba-127">Custom Serialization</span></span>](../../../docs/standard/serialization/custom-serialization.md)  
 <span data-ttu-id="020ba-128">Popisuje, jak přizpůsobit serializace pro třídu pomocí <xref:System.Runtime.Serialization.ISerializable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="020ba-128">Describes how to customize serialization for a class by using the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>  
  
 [<span data-ttu-id="020ba-129">Kroky v procesu serializace</span><span class="sxs-lookup"><span data-stu-id="020ba-129">Steps in the Serialization Process</span></span>](../../../docs/standard/serialization/steps-in-the-serialization-process.md)  
 <span data-ttu-id="020ba-130">Popisuje kurz akce serializace trvá, když <xref:System.Runtime.Serialization.Formatter.Serialize%2A> metoda je volána na formátovacím modulem.</span><span class="sxs-lookup"><span data-stu-id="020ba-130">Describes the course of action serialization takes when the <xref:System.Runtime.Serialization.Formatter.Serialize%2A> method is called on a formatter.</span></span>  
  
 [<span data-ttu-id="020ba-131">Verze serializace</span><span class="sxs-lookup"><span data-stu-id="020ba-131">Version Tolerant Serialization</span></span>](../../../docs/standard/serialization/version-tolerant-serialization.md)  
 <span data-ttu-id="020ba-132">Vysvětluje, jak vytvořit Serializovatelné typy, které lze upravit v čase bez způsobení aplikací k vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="020ba-132">Explains how to create serializable types that can be modified over time without causing applications to throw exceptions.</span></span>  
  
 [<span data-ttu-id="020ba-133">Pokyny pro serializaci</span><span class="sxs-lookup"><span data-stu-id="020ba-133">Serialization Guidelines</span></span>](../../../docs/standard/serialization/serialization-guidelines.md)  
 <span data-ttu-id="020ba-134">Poskytuje některé obecné pokyny pro rozhodování, kdy k serializaci objektu.</span><span class="sxs-lookup"><span data-stu-id="020ba-134">Provides some general guidelines for deciding when to serialize an object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="020ba-135">Odkaz</span><span class="sxs-lookup"><span data-stu-id="020ba-135">Reference</span></span>  
 <xref:System.Runtime.Serialization>  
 <span data-ttu-id="020ba-136">Obsahuje třídy, které lze použít pro serializaci a deserializaci objektů.</span><span class="sxs-lookup"><span data-stu-id="020ba-136">Contains classes that can be used for serializing and deserializing objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="020ba-137">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="020ba-137">Related sections</span></span>  
 [<span data-ttu-id="020ba-138">XML a serializace protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="020ba-138">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 <span data-ttu-id="020ba-139">Popisuje mechanismus serializace XML, který je součástí common language runtime.</span><span class="sxs-lookup"><span data-stu-id="020ba-139">Describes the XML serialization mechanism that is included with the common language runtime.</span></span>  
  
 [<span data-ttu-id="020ba-140">Zabezpečení a serializace</span><span class="sxs-lookup"><span data-stu-id="020ba-140">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)  
 <span data-ttu-id="020ba-141">Popisuje zabezpečené kódování zásady dodržovat při psaní kódu, který provede serializaci.</span><span class="sxs-lookup"><span data-stu-id="020ba-141">Describes the secure coding guidelines to follow when writing code that performs serialization.</span></span>  
  
 [<span data-ttu-id="020ba-142">Vzdálených objektů</span><span class="sxs-lookup"><span data-stu-id="020ba-142">Remote Objects</span></span>](http://msdn.microsoft.com/en-us/515686e6-0a8d-42f7-8188-73abede57c58)  
 <span data-ttu-id="020ba-143">Popisuje různé komunikační metody k dispozici v rozhraní .NET Framework pro vzdálenou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="020ba-143">Describes the various communications methods available in the .NET Framework for remote communications.</span></span>  
  
 [<span data-ttu-id="020ba-144">Webové služby XML vytvořený pomocí technologie ASP.NET a klienty webové služby XML</span><span class="sxs-lookup"><span data-stu-id="020ba-144">XML Web Services Created Using ASP.NET and XML Web Service Clients</span></span>](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)  
 <span data-ttu-id="020ba-145">Obsahuje témata, která popisují a popisují, jak program webové služby XML vytvořených pomocí technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="020ba-145">Provides topics that describe and explain how to program XML Web services created using ASP.NET.</span></span>
