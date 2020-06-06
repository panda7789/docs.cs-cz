---
title: Binární serializace
description: Tento článek popisuje binární serializaci a typy, pro které je rozhraní .NET Core podporuje. Mějte na paměti, že se nejedná o nebezpečí binární serializace a alternativ.
ms.date: 01/02/2018
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
author: ViktorHofer
ms.openlocfilehash: c735d30920fd3c8cd13243b4a5a29489ce05b262
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289691"
---
# <a name="binary-serialization"></a><span data-ttu-id="616d7-104">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="616d7-104">Binary serialization</span></span>

<span data-ttu-id="616d7-105">Serializace může být definován jako proces ukládání stavu objektu do úložiště média.</span><span class="sxs-lookup"><span data-stu-id="616d7-105">Serialization can be defined as the process of storing the state of an object to a storage medium.</span></span> <span data-ttu-id="616d7-106">Během tohoto procesu se veřejné a soukromé pole objektu a název třídy, včetně sestavení obsahující dané třídy, jsou převedeny do datového proudu bajtů, které jsou následně zapsána do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="616d7-106">During this process, the public and private fields of the object and the name of the class, including the assembly containing the class, are converted to a stream of bytes, which is then written to a data stream.</span></span> <span data-ttu-id="616d7-107">Při objektu je následně deserializovat, je vytvořena přesné klon původní objekt.</span><span class="sxs-lookup"><span data-stu-id="616d7-107">When the object is subsequently deserialized, an exact clone of the original object is created.</span></span>

<span data-ttu-id="616d7-108">Při provádění mechanismus serializace v prostředí objektově orientované, je třeba vytvořit počet kompromisy mezi snadnost použití a flexibilitu.</span><span class="sxs-lookup"><span data-stu-id="616d7-108">When implementing a serialization mechanism in an object-oriented environment, you have to make a number of tradeoffs between ease of use and flexibility.</span></span> <span data-ttu-id="616d7-109">Proces můžete automatizované do značné míry, za předpokladu, že budete mít dostatečné kontrolu nad procesem.</span><span class="sxs-lookup"><span data-stu-id="616d7-109">The process can be automated to a large extent, provided you are given sufficient control over the process.</span></span> <span data-ttu-id="616d7-110">Například může nastat situace, kde jednoduché binární serializace není dostatečné, nebo mohou existovat konkrétní důvod, proč se rozhodnout, která pole v třídě muset být serializován.</span><span class="sxs-lookup"><span data-stu-id="616d7-110">For example, situations may arise where simple binary serialization is not sufficient, or there might be a specific reason to decide which fields in a class need to be serialized.</span></span> <span data-ttu-id="616d7-111">Následující části prozkoumají robustní mechanizmus serializace, který je součástí .NET, a zvýrazní celou řadu důležitých funkcí, které vám umožní přizpůsobit proces tak, aby vyhovoval vašim potřebám.</span><span class="sxs-lookup"><span data-stu-id="616d7-111">The following sections examine the robust serialization mechanism provided with .NET and highlight a number of important features that allow you to customize the process to meet your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="616d7-112">Stav UTF-8 nebo UTF-7 objekt není zachováváno, je-li objekt je serializaci a deserializaci pomocí různých verzí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="616d7-112">The state of a UTF-8 or UTF-7 encoded object is not preserved if the object is serialized and deserialized using different .NET Framework versions.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="616d7-113">Binární serializace umožňuje upravovat soukromé členy uvnitř objektu, a proto mění stav.</span><span class="sxs-lookup"><span data-stu-id="616d7-113">Binary serialization allows modifying private members inside an object and therefore changing the state of it.</span></span> <span data-ttu-id="616d7-114">Z tohoto důvodu jsou doporučeny jiné architektury serializace, jako <xref:System.Text.Json?displayProperty=fullName> například, které fungují na veřejné ploše rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="616d7-114">Because of this, other serialization frameworks, like <xref:System.Text.Json?displayProperty=fullName>, that operate on the public API surface are recommended.</span></span>

## <a name="net-core"></a><span data-ttu-id="616d7-115">.NET Core</span><span class="sxs-lookup"><span data-stu-id="616d7-115">.NET Core</span></span>

<span data-ttu-id="616d7-116">.NET Core podporuje binární serializaci pro podmnožinu typů.</span><span class="sxs-lookup"><span data-stu-id="616d7-116">.NET Core supports binary serialization for a subset of types.</span></span> <span data-ttu-id="616d7-117">Seznam podporovaných typů můžete zobrazit v níže uvedené části [serializovatelný typy](#serializable-types) .</span><span class="sxs-lookup"><span data-stu-id="616d7-117">You can see the list of supported types in the [Serializable types](#serializable-types) section that follows.</span></span> <span data-ttu-id="616d7-118">U uvedených typů je zaručena serializace mezi .NET Framework 4.5.1 a novějšími verzemi a mezi .NET Core 2,0 a novějšími verzemi.</span><span class="sxs-lookup"><span data-stu-id="616d7-118">The listed types are guaranteed to be serializable between .NET Framework 4.5.1 and later versions and between .NET Core 2.0 and later versions.</span></span> <span data-ttu-id="616d7-119">Jiné implementace rozhraní .NET, jako je například mono, nejsou oficiálně podporovány, ale měly by také fungovat.</span><span class="sxs-lookup"><span data-stu-id="616d7-119">Other .NET implementations, such as Mono, aren't officially supported but should also work.</span></span>

### <a name="serializable-types"></a><span data-ttu-id="616d7-120">Serializovatelné typy</span><span class="sxs-lookup"><span data-stu-id="616d7-120">Serializable types</span></span>

> [!div class="mx-tdCol2BreakAll"]
> | <span data-ttu-id="616d7-121">Typ</span><span class="sxs-lookup"><span data-stu-id="616d7-121">Type</span></span> | <span data-ttu-id="616d7-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="616d7-122">Notes</span></span> |
> | - | - |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderException?displayProperty=nameWithType> | <span data-ttu-id="616d7-123">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-123">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderInternalCompilerException?displayProperty=nameWithType> | <span data-ttu-id="616d7-124">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-124">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AccessViolationException?displayProperty=nameWithType> | <span data-ttu-id="616d7-125">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-125">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AggregateException?displayProperty=nameWithType> | <span data-ttu-id="616d7-126">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-126">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="616d7-127">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-127">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ApplicationException?displayProperty=nameWithType> | <span data-ttu-id="616d7-128">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-128">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentException?displayProperty=nameWithType> | <span data-ttu-id="616d7-129">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-129">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentNullException?displayProperty=nameWithType> | <span data-ttu-id="616d7-130">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-130">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="616d7-131">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-131">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArithmeticException?displayProperty=nameWithType> | <span data-ttu-id="616d7-132">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-132">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Array?displayProperty=nameWithType> | |
> | <xref:System.ArraySegment%601?displayProperty=nameWithType> | |
> | <xref:System.ArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="616d7-133">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-133">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Attribute?displayProperty=nameWithType> | |
> | <xref:System.BadImageFormatException?displayProperty=nameWithType> | <span data-ttu-id="616d7-134">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-134">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Boolean?displayProperty=nameWithType> | |
> | <xref:System.Byte?displayProperty=nameWithType> | |
> | <xref:System.CannotUnloadAppDomainException?displayProperty=nameWithType> | <span data-ttu-id="616d7-135">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-135">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Char?displayProperty=nameWithType> | |
> | <xref:System.Collections.ArrayList?displayProperty=nameWithType> | |
> | <xref:System.Collections.BitArray?displayProperty=nameWithType> | |
> | <xref:System.Collections.Comparer?displayProperty=nameWithType> | |
> | <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="616d7-136">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-136">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Hashtable?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Queue?displayProperty=nameWithType> | |
> | <xref:System.Collections.SortedList?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Stack?displayProperty=nameWithType> | |
> | `System.Collections.Generic.NonRandomizedStringEqualityComparer` | <span data-ttu-id="616d7-137">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-137">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType> | |
> | <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType> | <span data-ttu-id="616d7-138">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-138">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Design.CheckoutException?displayProperty=nameWithType> | <span data-ttu-id="616d7-139">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-139">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidAsynchronousStateException?displayProperty=nameWithType> | <span data-ttu-id="616d7-140">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-140">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=nameWithType> | <span data-ttu-id="616d7-141">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-141">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.LicenseException?displayProperty=nameWithType> | <span data-ttu-id="616d7-142">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-142">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="616d7-143">Serializace z .NET Framework do .NET Core není podporována.</span><span class="sxs-lookup"><span data-stu-id="616d7-143">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.ComponentModel.WarningException?displayProperty=nameWithType> | <span data-ttu-id="616d7-144">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-144">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Win32Exception?displayProperty=nameWithType> | <span data-ttu-id="616d7-145">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-145">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType> | <span data-ttu-id="616d7-146">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-146">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationException?displayProperty=nameWithType> | <span data-ttu-id="616d7-147">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-147">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.Provider.ProviderException?displayProperty=nameWithType> | <span data-ttu-id="616d7-148">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-148">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyIsReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="616d7-149">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-149">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="616d7-150">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-150">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyWrongTypeException?displayProperty=nameWithType> | <span data-ttu-id="616d7-151">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-151">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ContextMarshalException?displayProperty=nameWithType> | <span data-ttu-id="616d7-152">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-152">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DBNull?displayProperty=nameWithType> | <span data-ttu-id="616d7-153">Počínaje .NET Core 2.0.2 a novějšími verzemi.</span><span class="sxs-lookup"><span data-stu-id="616d7-153">Starting in .NET Core 2.0.2 and later versions.</span></span> |
> | <xref:System.Data.Common.DbException?displayProperty=nameWithType> | <span data-ttu-id="616d7-154">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-154">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.ConstraintException?displayProperty=nameWithType> | <span data-ttu-id="616d7-155">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-155">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DBConcurrencyException?displayProperty=nameWithType> | <span data-ttu-id="616d7-156">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-156">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataException?displayProperty=nameWithType> | <span data-ttu-id="616d7-157">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-157">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataSet?displayProperty=nameWithType> | |
> | <xref:System.Data.DataTable?displayProperty=nameWithType> | <span data-ttu-id="616d7-158">Pokud nastavíte `RemotingFormat` `SerializationFormat.Binary` , můžete ho vyměnit jenom pomocí .net Core 2,1 a novějších verzí.</span><span class="sxs-lookup"><span data-stu-id="616d7-158">If you set `RemotingFormat` to `SerializationFormat.Binary`, it can only be exchanged with .NET Core 2.1 and later versions.</span></span> |
> | <xref:System.Data.DeletedRowInaccessibleException?displayProperty=nameWithType> | <span data-ttu-id="616d7-159">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-159">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DuplicateNameException?displayProperty=nameWithType> | <span data-ttu-id="616d7-160">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-160">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.EvaluateException?displayProperty=nameWithType> | <span data-ttu-id="616d7-161">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-161">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InRowChangingEventException?displayProperty=nameWithType> | <span data-ttu-id="616d7-162">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-162">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidConstraintException?displayProperty=nameWithType> | <span data-ttu-id="616d7-163">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-163">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidExpressionException?displayProperty=nameWithType> | <span data-ttu-id="616d7-164">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-164">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.MissingPrimaryKeyException?displayProperty=nameWithType> | <span data-ttu-id="616d7-165">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-165">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.NoNullAllowedException?displayProperty=nameWithType> | <span data-ttu-id="616d7-166">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-166">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.Odbc.OdbcException?displayProperty=nameWithType> | <span data-ttu-id="616d7-167">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-167">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.OperationAbortedException?displayProperty=nameWithType> | <span data-ttu-id="616d7-168">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-168">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.PropertyCollection?displayProperty=nameWithType> | |
> | <xref:System.Data.ReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="616d7-169">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-169">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.RowNotInTableException?displayProperty=nameWithType> | <span data-ttu-id="616d7-170">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-170">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlClient.SqlException?displayProperty=nameWithType> | <span data-ttu-id="616d7-171">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-171">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="616d7-172">Serializace z .NET Framework do .NET Core není podporována.</span><span class="sxs-lookup"><span data-stu-id="616d7-172">Serialization from .NET Framework to .NET Core is not supported</span></span> |
> | <xref:System.Data.SqlTypes.SqlAlreadyFilledException?displayProperty=nameWithType> | <span data-ttu-id="616d7-173">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-173">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlNotFilledException?displayProperty=nameWithType> | <span data-ttu-id="616d7-174">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-174">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlNullValueException?displayProperty=nameWithType> | <span data-ttu-id="616d7-175">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-175">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlTruncateException?displayProperty=nameWithType> | <span data-ttu-id="616d7-176">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-176">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlTypeException?displayProperty=nameWithType> | <span data-ttu-id="616d7-177">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-177">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.StrongTypingException?displayProperty=nameWithType> | <span data-ttu-id="616d7-178">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-178">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SyntaxErrorException?displayProperty=nameWithType> | <span data-ttu-id="616d7-179">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-179">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.VersionNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="616d7-180">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-180">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DataMisalignedException?displayProperty=nameWithType> | <span data-ttu-id="616d7-181">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-181">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DateTime?displayProperty=nameWithType> | |
> | <xref:System.DateTimeOffset?displayProperty=nameWithType> | |
> | <xref:System.Decimal?displayProperty=nameWithType> | |
> | `System.Diagnostics.Contracts.ContractException` | <span data-ttu-id="616d7-182">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-182">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Diagnostics.Tracing.EventSourceException?displayProperty=nameWithType> | <span data-ttu-id="616d7-183">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-183">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="616d7-184">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-184">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.MultipleMatchesException?displayProperty=nameWithType> | <span data-ttu-id="616d7-185">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-185">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.NoMatchingPrincipalException?displayProperty=nameWithType> | <span data-ttu-id="616d7-186">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-186">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PasswordException?displayProperty=nameWithType> | <span data-ttu-id="616d7-187">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-187">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalException?displayProperty=nameWithType> | <span data-ttu-id="616d7-188">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-188">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalExistsException?displayProperty=nameWithType> | <span data-ttu-id="616d7-189">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-189">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalOperationException?displayProperty=nameWithType> | <span data-ttu-id="616d7-190">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-190">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalServerDownException?displayProperty=nameWithType> | <span data-ttu-id="616d7-191">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-191">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectExistsException?displayProperty=nameWithType> | <span data-ttu-id="616d7-192">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-192">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="616d7-193">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-193">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="616d7-194">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-194">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryServerDownException?displayProperty=nameWithType> | <span data-ttu-id="616d7-195">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-195">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ForestTrustCollisionException?displayProperty=nameWithType> | <span data-ttu-id="616d7-196">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-196">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.SyncFromAllServersOperationException?displayProperty=nameWithType> | <span data-ttu-id="616d7-197">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-197">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.DirectoryServicesCOMException?displayProperty=nameWithType> | <span data-ttu-id="616d7-198">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-198">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.BerConversionException?displayProperty=nameWithType> | <span data-ttu-id="616d7-199">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-199">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryException?displayProperty=nameWithType> | <span data-ttu-id="616d7-200">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-200">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="616d7-201">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-201">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.LdapException?displayProperty=nameWithType> | <span data-ttu-id="616d7-202">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-202">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.TlsOperationException?displayProperty=nameWithType> | <span data-ttu-id="616d7-203">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-203">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DivideByZeroException?displayProperty=nameWithType> | <span data-ttu-id="616d7-204">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-204">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DllNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="616d7-205">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-205">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Double?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Color?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Point?displayProperty=nameWithType> | |
> | <xref:System.Drawing.PointF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Rectangle?displayProperty=nameWithType> | |
> | <xref:System.Drawing.RectangleF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Size?displayProperty=nameWithType> | |
> | <xref:System.Drawing.SizeF?displayProperty=nameWithType> | |
> | <xref:System.DuplicateWaitObjectException?displayProperty=nameWithType> | <span data-ttu-id="616d7-206">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-206">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.EntryPointNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="616d7-207">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-207">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Enum?displayProperty=nameWithType> | |
> | <xref:System.EventArgs?displayProperty=nameWithType> | <span data-ttu-id="616d7-208">Začíná v .NET Core 2.0.6.</span><span class="sxs-lookup"><span data-stu-id="616d7-208">Starting in .NET Core 2.0.6.</span></span> |
> | <xref:System.Exception?displayProperty=nameWithType> | |
> | <xref:System.ExecutionEngineException?displayProperty=nameWithType> | <span data-ttu-id="616d7-209">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-209">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FieldAccessException?displayProperty=nameWithType> | <span data-ttu-id="616d7-210">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-210">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FormatException?displayProperty=nameWithType> | <span data-ttu-id="616d7-211">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-211">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> | |
> | <xref:System.Globalization.CultureNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="616d7-212">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-212">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.SortVersion?displayProperty=nameWithType> | |
> | <xref:System.Guid?displayProperty=nameWithType> | |
> | `System.IO.Compression.ZLibException` | <span data-ttu-id="616d7-213">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-213">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DriveNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="616d7-214">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-214">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.EndOfStreamException?displayProperty=nameWithType> | <span data-ttu-id="616d7-215">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-215">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileFormatException?displayProperty=nameWithType> | <span data-ttu-id="616d7-216">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-216">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileLoadException?displayProperty=nameWithType> | <span data-ttu-id="616d7-217">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-217">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="616d7-218">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-218">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IOException?displayProperty=nameWithType> | <span data-ttu-id="616d7-219">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-219">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InternalBufferOverflowException?displayProperty=nameWithType> | <span data-ttu-id="616d7-220">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-220">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InvalidDataException?displayProperty=nameWithType> | <span data-ttu-id="616d7-221">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-221">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IsolatedStorage.IsolatedStorageException?displayProperty=nameWithType> | <span data-ttu-id="616d7-222">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-222">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.PathTooLongException?displayProperty=nameWithType> | <span data-ttu-id="616d7-223">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-223">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="616d7-224">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-224">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientExecutionStackException?displayProperty=nameWithType> | <span data-ttu-id="616d7-225">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-225">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientMemoryException?displayProperty=nameWithType> | <span data-ttu-id="616d7-226">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-226">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Int16?displayProperty=nameWithType> | |
> | <xref:System.Int32?displayProperty=nameWithType> | |
> | <xref:System.Int64?displayProperty=nameWithType> | |
> | <xref:System.IntPtr?displayProperty=nameWithType> | |
> | <xref:System.InvalidCastException?displayProperty=nameWithType> | <span data-ttu-id="616d7-227">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-227">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidOperationException?displayProperty=nameWithType> | <span data-ttu-id="616d7-228">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-228">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidProgramException?displayProperty=nameWithType> | <span data-ttu-id="616d7-229">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-229">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidTimeZoneException?displayProperty=nameWithType> | <span data-ttu-id="616d7-230">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-230">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MemberAccessException?displayProperty=nameWithType> | <span data-ttu-id="616d7-231">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-231">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MethodAccessException?displayProperty=nameWithType> | <span data-ttu-id="616d7-232">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-232">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingFieldException?displayProperty=nameWithType> | <span data-ttu-id="616d7-233">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-233">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMemberException?displayProperty=nameWithType> | <span data-ttu-id="616d7-234">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-234">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMethodException?displayProperty=nameWithType> | <span data-ttu-id="616d7-235">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-235">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MulticastNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="616d7-236">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-236">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Cookie?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieCollection?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieContainer?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieException?displayProperty=nameWithType> | <span data-ttu-id="616d7-237">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-237">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.HttpListenerException?displayProperty=nameWithType> | <span data-ttu-id="616d7-238">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-238">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpException?displayProperty=nameWithType> | <span data-ttu-id="616d7-239">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-239">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientException?displayProperty=nameWithType> | <span data-ttu-id="616d7-240">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-240">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientsException?displayProperty=nameWithType> | <span data-ttu-id="616d7-241">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-241">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.NetworkInformationException?displayProperty=nameWithType> | <span data-ttu-id="616d7-242">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-242">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.PingException?displayProperty=nameWithType> | <span data-ttu-id="616d7-243">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-243">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.ProtocolViolationException?displayProperty=nameWithType> | <span data-ttu-id="616d7-244">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-244">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Sockets.SocketException?displayProperty=nameWithType> | <span data-ttu-id="616d7-245">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-245">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebException?displayProperty=nameWithType> | <span data-ttu-id="616d7-246">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-246">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebSockets.WebSocketException?displayProperty=nameWithType> | <span data-ttu-id="616d7-247">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-247">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotFiniteNumberException?displayProperty=nameWithType> | <span data-ttu-id="616d7-248">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-248">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotImplementedException?displayProperty=nameWithType> | <span data-ttu-id="616d7-249">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-249">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="616d7-250">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-250">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NullReferenceException?displayProperty=nameWithType> | <span data-ttu-id="616d7-251">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-251">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Nullable%601?displayProperty=nameWithType> | |
> | <xref:System.Numerics.BigInteger?displayProperty=nameWithType> | |
> | <xref:System.Numerics.Complex?displayProperty=nameWithType> | |
> | <xref:System.Object?displayProperty=nameWithType> | |
> | <xref:System.ObjectDisposedException?displayProperty=nameWithType> | <span data-ttu-id="616d7-252">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-252">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OperationCanceledException?displayProperty=nameWithType> | <span data-ttu-id="616d7-253">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-253">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OutOfMemoryException?displayProperty=nameWithType> | <span data-ttu-id="616d7-254">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-254">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OverflowException?displayProperty=nameWithType> | <span data-ttu-id="616d7-255">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-255">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.PlatformNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="616d7-256">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-256">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.RankException?displayProperty=nameWithType> | <span data-ttu-id="616d7-257">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-257">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.AmbiguousMatchException?displayProperty=nameWithType> | <span data-ttu-id="616d7-258">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-258">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.CustomAttributeFormatException?displayProperty=nameWithType> | <span data-ttu-id="616d7-259">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-259">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.InvalidFilterCriteriaException?displayProperty=nameWithType> | <span data-ttu-id="616d7-260">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-260">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.ReflectionTypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="616d7-261">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-261">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="616d7-262">Serializace z .NET Framework do .NET Core není podporována.</span><span class="sxs-lookup"><span data-stu-id="616d7-262">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.Reflection.TargetException?displayProperty=nameWithType> | <span data-ttu-id="616d7-263">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-263">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetInvocationException?displayProperty=nameWithType> | <span data-ttu-id="616d7-264">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-264">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetParameterCountException?displayProperty=nameWithType> | <span data-ttu-id="616d7-265">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-265">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingManifestResourceException?displayProperty=nameWithType> | <span data-ttu-id="616d7-266">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-266">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingSatelliteAssemblyException?displayProperty=nameWithType> | <span data-ttu-id="616d7-267">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-267">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.CompilerServices.RuntimeWrappedException?displayProperty=nameWithType> | <span data-ttu-id="616d7-268">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-268">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.COMException?displayProperty=nameWithType> | <span data-ttu-id="616d7-269">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-269">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.ExternalException?displayProperty=nameWithType> | <span data-ttu-id="616d7-270">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-270">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidComObjectException?displayProperty=nameWithType> | <span data-ttu-id="616d7-271">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-271">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidOleVariantTypeException?displayProperty=nameWithType> | <span data-ttu-id="616d7-272">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-272">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.MarshalDirectiveException?displayProperty=nameWithType> | <span data-ttu-id="616d7-273">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-273">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SEHException?displayProperty=nameWithType> | <span data-ttu-id="616d7-274">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-274">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException?displayProperty=nameWithType> | <span data-ttu-id="616d7-275">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-275">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="616d7-276">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-276">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.InvalidDataContractException?displayProperty=nameWithType> | <span data-ttu-id="616d7-277">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-277">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.SerializationException?displayProperty=nameWithType> | <span data-ttu-id="616d7-278">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-278">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.SByte?displayProperty=nameWithType> | |
> | <xref:System.Security.AccessControl.PrivilegeNotHeldException?displayProperty=nameWithType> | <span data-ttu-id="616d7-279">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-279">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.AuthenticationException?displayProperty=nameWithType> | <span data-ttu-id="616d7-280">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-280">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.InvalidCredentialException?displayProperty=nameWithType> | <span data-ttu-id="616d7-281">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-281">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicException?displayProperty=nameWithType> | <span data-ttu-id="616d7-282">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-282">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicUnexpectedOperationException?displayProperty=nameWithType> | <span data-ttu-id="616d7-283">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-283">Starting in .NET Core 2.0.4.</span></span> |
> | `System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException` | <span data-ttu-id="616d7-284">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-284">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.HostProtectionException?displayProperty=nameWithType> | <span data-ttu-id="616d7-285">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-285">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Policy.PolicyException?displayProperty=nameWithType> | <span data-ttu-id="616d7-286">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-286">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Principal.IdentityNotMappedException?displayProperty=nameWithType> | <span data-ttu-id="616d7-287">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-287">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.SecurityException?displayProperty=nameWithType> | <span data-ttu-id="616d7-288">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-288">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="616d7-289">Omezená data serializace.</span><span class="sxs-lookup"><span data-stu-id="616d7-289">Limited serialization data.</span></span> |
> | <xref:System.Security.VerificationException?displayProperty=nameWithType> | <span data-ttu-id="616d7-290">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-290">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.XmlSyntaxException?displayProperty=nameWithType> | <span data-ttu-id="616d7-291">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-291">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ServiceProcess.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="616d7-292">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-292">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Single?displayProperty=nameWithType> | |
> | <xref:System.StackOverflowException?displayProperty=nameWithType> | <span data-ttu-id="616d7-293">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-293">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.String?displayProperty=nameWithType> | |
> | <xref:System.StringComparer?displayProperty=nameWithType> | |
> | <xref:System.SystemException?displayProperty=nameWithType> | <span data-ttu-id="616d7-294">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-294">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.DecoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="616d7-295">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-295">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.EncoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="616d7-296">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-296">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.RegularExpressions.RegexMatchTimeoutException?displayProperty=nameWithType> | <span data-ttu-id="616d7-297">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-297">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.StringBuilder?displayProperty=nameWithType> | |
> | <xref:System.Threading.AbandonedMutexException?displayProperty=nameWithType> | <span data-ttu-id="616d7-298">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-298">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.BarrierPostPhaseException?displayProperty=nameWithType> | <span data-ttu-id="616d7-299">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-299">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.LockRecursionException?displayProperty=nameWithType> | <span data-ttu-id="616d7-300">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-300">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SemaphoreFullException?displayProperty=nameWithType> | <span data-ttu-id="616d7-301">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-301">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SynchronizationLockException?displayProperty=nameWithType> | <span data-ttu-id="616d7-302">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-302">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> | <span data-ttu-id="616d7-303">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-303">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskSchedulerException?displayProperty=nameWithType> | <span data-ttu-id="616d7-304">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-304">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> | <span data-ttu-id="616d7-305">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-305">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadInterruptedException?displayProperty=nameWithType> | <span data-ttu-id="616d7-306">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-306">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStartException?displayProperty=nameWithType> | <span data-ttu-id="616d7-307">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-307">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStateException?displayProperty=nameWithType> | <span data-ttu-id="616d7-308">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-308">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.WaitHandleCannotBeOpenedException?displayProperty=nameWithType> | <span data-ttu-id="616d7-309">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-309">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeSpan?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="616d7-310">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-310">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="616d7-311">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-311">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionAbortedException?displayProperty=nameWithType> | <span data-ttu-id="616d7-312">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-312">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionException?displayProperty=nameWithType> | <span data-ttu-id="616d7-313">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-313">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionInDoubtException?displayProperty=nameWithType> | <span data-ttu-id="616d7-314">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-314">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionManagerCommunicationException?displayProperty=nameWithType> | <span data-ttu-id="616d7-315">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-315">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionPromotionException?displayProperty=nameWithType> | <span data-ttu-id="616d7-316">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-316">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Tuple?displayProperty=nameWithType> | |
> | <xref:System.TypeAccessException?displayProperty=nameWithType> | <span data-ttu-id="616d7-317">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-317">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeInitializationException?displayProperty=nameWithType> | <span data-ttu-id="616d7-318">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-318">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="616d7-319">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-319">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="616d7-320">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-320">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.UInt16?displayProperty=nameWithType> | |
> | <xref:System.UInt32?displayProperty=nameWithType> | |
> | <xref:System.UInt64?displayProperty=nameWithType> | |
> | <xref:System.UIntPtr?displayProperty=nameWithType> | |
> | <xref:System.UnauthorizedAccessException?displayProperty=nameWithType> | <span data-ttu-id="616d7-321">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-321">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Uri?displayProperty=nameWithType> | |
> | <xref:System.UriFormatException?displayProperty=nameWithType> | <span data-ttu-id="616d7-322">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-322">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ValueTuple?displayProperty=nameWithType> | <span data-ttu-id="616d7-323">Nelze serializovat v .NET Framework 4,7 a dřívějších verzích.</span><span class="sxs-lookup"><span data-stu-id="616d7-323">Not serializable in .NET Framework 4.7 and earlier versions.</span></span> |
> | <xref:System.ValueType?displayProperty=nameWithType> | |
> | <xref:System.Version?displayProperty=nameWithType> | |
> | <xref:System.WeakReference%601?displayProperty=nameWithType> | |
> | <xref:System.WeakReference?displayProperty=nameWithType> | |
> | <xref:System.Xml.Schema.XmlSchemaException?displayProperty=nameWithType> | <span data-ttu-id="616d7-324">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-324">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaInferenceException?displayProperty=nameWithType> | <span data-ttu-id="616d7-325">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-325">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaValidationException?displayProperty=nameWithType> | <span data-ttu-id="616d7-326">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-326">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XPath.XPathException?displayProperty=nameWithType> | <span data-ttu-id="616d7-327">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-327">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XmlException?displayProperty=nameWithType> | <span data-ttu-id="616d7-328">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-328">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltCompileException?displayProperty=nameWithType> | <span data-ttu-id="616d7-329">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-329">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltException?displayProperty=nameWithType> | <span data-ttu-id="616d7-330">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="616d7-330">Starting in .NET Core 2.0.4.</span></span> |

## <a name="see-also"></a><span data-ttu-id="616d7-331">Viz také</span><span class="sxs-lookup"><span data-stu-id="616d7-331">See also</span></span>

- <xref:System.Runtime.Serialization>\
<span data-ttu-id="616d7-332">Obsahuje třídy, které lze použít pro serializaci a deserializaci objektů.</span><span class="sxs-lookup"><span data-stu-id="616d7-332">Contains classes that can be used for serializing and deserializing objects.</span></span>

- <span data-ttu-id="616d7-333">[Serializace XML a SOAP](xml-and-soap-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="616d7-333">[XML and SOAP Serialization](xml-and-soap-serialization.md)</span></span>\
<span data-ttu-id="616d7-334">Popisuje mechanismus serializace XML, který je součástí common language runtime.</span><span class="sxs-lookup"><span data-stu-id="616d7-334">Describes the XML serialization mechanism that is included with the common language runtime.</span></span>

- <span data-ttu-id="616d7-335">[Zabezpečení a serializace](../../framework/misc/security-and-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="616d7-335">[Security and Serialization](../../framework/misc/security-and-serialization.md)</span></span>\
<span data-ttu-id="616d7-336">Popisuje zabezpečené kódování zásady dodržovat při psaní kódu, který provede serializaci.</span><span class="sxs-lookup"><span data-stu-id="616d7-336">Describes the secure coding guidelines to follow when writing code that performs serialization.</span></span>

- <span data-ttu-id="616d7-337">[Vzdálená komunikace .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="616d7-337">[.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span></span>\
<span data-ttu-id="616d7-338">V této části najdete popis různých metod, které se spouští v .NET Framework pro vzdálenou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="616d7-338">Describes the various methods Starting in .NET Framework for remote communications.</span></span>

- <span data-ttu-id="616d7-339">[Webové služby XML vytvořené pomocí ASP.NET a klientů webové služby XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="616d7-339">[XML Web Services Created Using ASP.NET and XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>\
<span data-ttu-id="616d7-340">Články, které popisují a vysvětlují, jak programovat webové služby XML pomocí ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="616d7-340">Articles that describe and explain how to program XML Web services created using ASP.NET.</span></span>
