---
title: Binární serializace
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
ms.openlocfilehash: 9df9b73a1a1347b952d76b76c9058578f5e9f401
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400636"
---
# <a name="binary-serialization"></a><span data-ttu-id="3584d-102">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="3584d-102">Binary serialization</span></span>

<span data-ttu-id="3584d-103">Serializace může být definován jako proces ukládání stavu objektu do úložiště média.</span><span class="sxs-lookup"><span data-stu-id="3584d-103">Serialization can be defined as the process of storing the state of an object to a storage medium.</span></span> <span data-ttu-id="3584d-104">Během tohoto procesu se veřejné a soukromé pole objektu a název třídy, včetně sestavení obsahující dané třídy, jsou převedeny do datového proudu bajtů, které jsou následně zapsána do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="3584d-104">During this process, the public and private fields of the object and the name of the class, including the assembly containing the class, are converted to a stream of bytes, which is then written to a data stream.</span></span> <span data-ttu-id="3584d-105">Při objektu je následně deserializovat, je vytvořena přesné klon původní objekt.</span><span class="sxs-lookup"><span data-stu-id="3584d-105">When the object is subsequently deserialized, an exact clone of the original object is created.</span></span>

<span data-ttu-id="3584d-106">Při provádění mechanismus serializace v prostředí objektově orientované, je třeba vytvořit počet kompromisy mezi snadnost použití a flexibilitu.</span><span class="sxs-lookup"><span data-stu-id="3584d-106">When implementing a serialization mechanism in an object-oriented environment, you have to make a number of tradeoffs between ease of use and flexibility.</span></span> <span data-ttu-id="3584d-107">Proces můžete automatizované do značné míry, za předpokladu, že budete mít dostatečné kontrolu nad procesem.</span><span class="sxs-lookup"><span data-stu-id="3584d-107">The process can be automated to a large extent, provided you are given sufficient control over the process.</span></span> <span data-ttu-id="3584d-108">Například může nastat situace, kde jednoduché binární serializace není dostatečné, nebo mohou existovat konkrétní důvod, proč se rozhodnout, která pole v třídě muset být serializován.</span><span class="sxs-lookup"><span data-stu-id="3584d-108">For example, situations may arise where simple binary serialization is not sufficient, or there might be a specific reason to decide which fields in a class need to be serialized.</span></span> <span data-ttu-id="3584d-109">V následujících částech zkontrolujte robustní serializační mechanismus dodávaný s rozhraním .NET a zvýrazněte řadu důležitých funkcí, které umožňují přizpůsobit proces vašim potřebám.</span><span class="sxs-lookup"><span data-stu-id="3584d-109">The following sections examine the robust serialization mechanism provided with .NET and highlight a number of important features that allow you to customize the process to meet your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="3584d-110">Stav UTF-8 nebo UTF-7 objekt není zachováváno, je-li objekt je serializaci a deserializaci pomocí různých verzí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3584d-110">The state of a UTF-8 or UTF-7 encoded object is not preserved if the object is serialized and deserialized using different .NET Framework versions.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="3584d-111">Binární serializace umožňuje úpravu soukromých členů uvnitř objektu a proto mění jeho stav.</span><span class="sxs-lookup"><span data-stu-id="3584d-111">Binary serialization allows modifying private members inside an object and therefore changing the state of it.</span></span> <span data-ttu-id="3584d-112">Z tohoto důvodu se doporučují další <xref:System.Text.Json?displayProperty=fullName>architektury serializace, jako je , které pracují na povrchu veřejného rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="3584d-112">Because of this, other serialization frameworks, like <xref:System.Text.Json?displayProperty=fullName>, that operate on the public API surface are recommended.</span></span>

## <a name="net-core"></a><span data-ttu-id="3584d-113">.NET Core</span><span class="sxs-lookup"><span data-stu-id="3584d-113">.NET Core</span></span>

<span data-ttu-id="3584d-114">Jádro .NET podporuje binární serializaci pro podmnožinu typů.</span><span class="sxs-lookup"><span data-stu-id="3584d-114">.NET Core supports binary serialization for a subset of types.</span></span> <span data-ttu-id="3584d-115">Seznam podporovaných typů naleznete v následující části [Serializovatelné typy.](#serializable-types)</span><span class="sxs-lookup"><span data-stu-id="3584d-115">You can see the list of supported types in the [Serializable types](#serializable-types) section that follows.</span></span> <span data-ttu-id="3584d-116">Uvedené typy jsou zaručeně serializovatelné mezi rozhraním .NET Framework 4.5.1 a novějšími verzemi a mezi verzemi .NET Core 2.0 a novějšími.</span><span class="sxs-lookup"><span data-stu-id="3584d-116">The listed types are guaranteed to be serializable between .NET Framework 4.5.1 and later versions and between .NET Core 2.0 and later versions.</span></span> <span data-ttu-id="3584d-117">Jiné implementace rozhraní .NET, například Mono, nejsou oficiálně podporovány, ale měly by také fungovat.</span><span class="sxs-lookup"><span data-stu-id="3584d-117">Other .NET implementations, such as Mono, aren't officially supported but should also work.</span></span>

### <a name="serializable-types"></a><span data-ttu-id="3584d-118">Serializovatelné typy</span><span class="sxs-lookup"><span data-stu-id="3584d-118">Serializable types</span></span>

> [!div class="mx-tdCol2BreakAll"]
> | <span data-ttu-id="3584d-119">Typ</span><span class="sxs-lookup"><span data-stu-id="3584d-119">Type</span></span> | <span data-ttu-id="3584d-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3584d-120">Notes</span></span> |
> | - | - |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderException?displayProperty=nameWithType> | <span data-ttu-id="3584d-121">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-121">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderInternalCompilerException?displayProperty=nameWithType> | <span data-ttu-id="3584d-122">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-122">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AccessViolationException?displayProperty=nameWithType> | <span data-ttu-id="3584d-123">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-123">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AggregateException?displayProperty=nameWithType> | <span data-ttu-id="3584d-124">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-124">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="3584d-125">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-125">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ApplicationException?displayProperty=nameWithType> | <span data-ttu-id="3584d-126">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-126">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentException?displayProperty=nameWithType> | <span data-ttu-id="3584d-127">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-127">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentNullException?displayProperty=nameWithType> | <span data-ttu-id="3584d-128">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-128">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="3584d-129">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-129">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArithmeticException?displayProperty=nameWithType> | <span data-ttu-id="3584d-130">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-130">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Array?displayProperty=nameWithType> | |
> | <xref:System.ArraySegment%601?displayProperty=nameWithType> | |
> | <xref:System.ArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="3584d-131">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-131">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Attribute?displayProperty=nameWithType> | |
> | <xref:System.BadImageFormatException?displayProperty=nameWithType> | <span data-ttu-id="3584d-132">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-132">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Boolean?displayProperty=nameWithType> | |
> | <xref:System.Byte?displayProperty=nameWithType> | |
> | <xref:System.CannotUnloadAppDomainException?displayProperty=nameWithType> | <span data-ttu-id="3584d-133">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-133">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Char?displayProperty=nameWithType> | |
> | <xref:System.Collections.ArrayList?displayProperty=nameWithType> | |
> | <xref:System.Collections.BitArray?displayProperty=nameWithType> | |
> | <xref:System.Collections.Comparer?displayProperty=nameWithType> | |
> | <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="3584d-134">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-134">Starting in .NET Core 2.0.4.</span></span> |
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
> | `System.Collections.Generic.NonRandomizedStringEqualityComparer` | <span data-ttu-id="3584d-135">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-135">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType> | |
> | <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType> | <span data-ttu-id="3584d-136">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-136">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Design.CheckoutException?displayProperty=nameWithType> | <span data-ttu-id="3584d-137">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-137">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidAsynchronousStateException?displayProperty=nameWithType> | <span data-ttu-id="3584d-138">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-138">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=nameWithType> | <span data-ttu-id="3584d-139">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-139">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.LicenseException?displayProperty=nameWithType> | <span data-ttu-id="3584d-140">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-140">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="3584d-141">Serializace z rozhraní .NET Framework na .NET Core není podporována.</span><span class="sxs-lookup"><span data-stu-id="3584d-141">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.ComponentModel.WarningException?displayProperty=nameWithType> | <span data-ttu-id="3584d-142">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-142">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Win32Exception?displayProperty=nameWithType> | <span data-ttu-id="3584d-143">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-143">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType> | <span data-ttu-id="3584d-144">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-144">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationException?displayProperty=nameWithType> | <span data-ttu-id="3584d-145">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-145">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.Provider.ProviderException?displayProperty=nameWithType> | <span data-ttu-id="3584d-146">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-146">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyIsReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="3584d-147">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-147">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="3584d-148">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-148">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyWrongTypeException?displayProperty=nameWithType> | <span data-ttu-id="3584d-149">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-149">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ContextMarshalException?displayProperty=nameWithType> | <span data-ttu-id="3584d-150">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-150">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DBNull?displayProperty=nameWithType> | <span data-ttu-id="3584d-151">Počínaje verzí .NET Core 2.0.2 a novějšími.</span><span class="sxs-lookup"><span data-stu-id="3584d-151">Starting in .NET Core 2.0.2 and later versions.</span></span> |
> | <xref:System.Data.Common.DbException?displayProperty=nameWithType> | <span data-ttu-id="3584d-152">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-152">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.ConstraintException?displayProperty=nameWithType> | <span data-ttu-id="3584d-153">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-153">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DBConcurrencyException?displayProperty=nameWithType> | <span data-ttu-id="3584d-154">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-154">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataException?displayProperty=nameWithType> | <span data-ttu-id="3584d-155">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-155">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataSet?displayProperty=nameWithType> | |
> | <xref:System.Data.DataTable?displayProperty=nameWithType> | <span data-ttu-id="3584d-156">Pokud nastavíte `RemotingFormat` `SerializationFormat.Binary`na , lze ji vyměnit pouze s rozhraním .NET Core 2.1 a novějšími verzemi.</span><span class="sxs-lookup"><span data-stu-id="3584d-156">If you set `RemotingFormat` to `SerializationFormat.Binary`, it can only be exchanged with .NET Core 2.1 and later versions.</span></span> |
> | <xref:System.Data.DeletedRowInaccessibleException?displayProperty=nameWithType> | <span data-ttu-id="3584d-157">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-157">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DuplicateNameException?displayProperty=nameWithType> | <span data-ttu-id="3584d-158">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-158">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.EvaluateException?displayProperty=nameWithType> | <span data-ttu-id="3584d-159">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-159">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InRowChangingEventException?displayProperty=nameWithType> | <span data-ttu-id="3584d-160">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-160">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidConstraintException?displayProperty=nameWithType> | <span data-ttu-id="3584d-161">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-161">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidExpressionException?displayProperty=nameWithType> | <span data-ttu-id="3584d-162">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-162">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.MissingPrimaryKeyException?displayProperty=nameWithType> | <span data-ttu-id="3584d-163">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-163">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.NoNullAllowedException?displayProperty=nameWithType> | <span data-ttu-id="3584d-164">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-164">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.Odbc.OdbcException?displayProperty=nameWithType> | <span data-ttu-id="3584d-165">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-165">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.OperationAbortedException?displayProperty=nameWithType> | <span data-ttu-id="3584d-166">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-166">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.PropertyCollection?displayProperty=nameWithType> | |
> | <xref:System.Data.ReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="3584d-167">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-167">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.RowNotInTableException?displayProperty=nameWithType> | <span data-ttu-id="3584d-168">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-168">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlClient.SqlException?displayProperty=nameWithType> | <span data-ttu-id="3584d-169">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-169">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="3584d-170">Serializace z rozhraní .NET Framework na jádro .NET není podporována.</span><span class="sxs-lookup"><span data-stu-id="3584d-170">Serialization from .NET Framework to .NET Core is not supported</span></span> |
> | <xref:System.Data.SqlTypes.SqlAlreadyFilledException?displayProperty=nameWithType> | <span data-ttu-id="3584d-171">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-171">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlNotFilledException?displayProperty=nameWithType> | <span data-ttu-id="3584d-172">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-172">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlNullValueException?displayProperty=nameWithType> | <span data-ttu-id="3584d-173">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-173">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlTruncateException?displayProperty=nameWithType> | <span data-ttu-id="3584d-174">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-174">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlTypeException?displayProperty=nameWithType> | <span data-ttu-id="3584d-175">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-175">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.StrongTypingException?displayProperty=nameWithType> | <span data-ttu-id="3584d-176">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-176">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SyntaxErrorException?displayProperty=nameWithType> | <span data-ttu-id="3584d-177">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-177">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.VersionNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="3584d-178">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-178">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DataMisalignedException?displayProperty=nameWithType> | <span data-ttu-id="3584d-179">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-179">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DateTime?displayProperty=nameWithType> | |
> | <xref:System.DateTimeOffset?displayProperty=nameWithType> | |
> | <xref:System.Decimal?displayProperty=nameWithType> | |
> | `System.Diagnostics.Contracts.ContractException` | <span data-ttu-id="3584d-180">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-180">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Diagnostics.Tracing.EventSourceException?displayProperty=nameWithType> | <span data-ttu-id="3584d-181">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-181">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="3584d-182">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-182">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.MultipleMatchesException?displayProperty=nameWithType> | <span data-ttu-id="3584d-183">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-183">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.NoMatchingPrincipalException?displayProperty=nameWithType> | <span data-ttu-id="3584d-184">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-184">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PasswordException?displayProperty=nameWithType> | <span data-ttu-id="3584d-185">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-185">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalException?displayProperty=nameWithType> | <span data-ttu-id="3584d-186">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-186">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalExistsException?displayProperty=nameWithType> | <span data-ttu-id="3584d-187">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-187">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalOperationException?displayProperty=nameWithType> | <span data-ttu-id="3584d-188">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-188">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalServerDownException?displayProperty=nameWithType> | <span data-ttu-id="3584d-189">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-189">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectExistsException?displayProperty=nameWithType> | <span data-ttu-id="3584d-190">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-190">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="3584d-191">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-191">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="3584d-192">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-192">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryServerDownException?displayProperty=nameWithType> | <span data-ttu-id="3584d-193">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-193">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ForestTrustCollisionException?displayProperty=nameWithType> | <span data-ttu-id="3584d-194">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-194">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.SyncFromAllServersOperationException?displayProperty=nameWithType> | <span data-ttu-id="3584d-195">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-195">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.DirectoryServicesCOMException?displayProperty=nameWithType> | <span data-ttu-id="3584d-196">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-196">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.BerConversionException?displayProperty=nameWithType> | <span data-ttu-id="3584d-197">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-197">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryException?displayProperty=nameWithType> | <span data-ttu-id="3584d-198">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-198">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="3584d-199">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-199">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.LdapException?displayProperty=nameWithType> | <span data-ttu-id="3584d-200">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-200">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.TlsOperationException?displayProperty=nameWithType> | <span data-ttu-id="3584d-201">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-201">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DivideByZeroException?displayProperty=nameWithType> | <span data-ttu-id="3584d-202">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-202">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DllNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="3584d-203">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-203">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Double?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Color?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Point?displayProperty=nameWithType> | |
> | <xref:System.Drawing.PointF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Rectangle?displayProperty=nameWithType> | |
> | <xref:System.Drawing.RectangleF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Size?displayProperty=nameWithType> | |
> | <xref:System.Drawing.SizeF?displayProperty=nameWithType> | |
> | <xref:System.DuplicateWaitObjectException?displayProperty=nameWithType> | <span data-ttu-id="3584d-204">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-204">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.EntryPointNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="3584d-205">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-205">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Enum?displayProperty=nameWithType> | |
> | <xref:System.EventArgs?displayProperty=nameWithType> | <span data-ttu-id="3584d-206">Počínaje rozhraním .NET Core 2.0.6.</span><span class="sxs-lookup"><span data-stu-id="3584d-206">Starting in .NET Core 2.0.6.</span></span> |
> | <xref:System.Exception?displayProperty=nameWithType> | |
> | <xref:System.ExecutionEngineException?displayProperty=nameWithType> | <span data-ttu-id="3584d-207">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-207">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FieldAccessException?displayProperty=nameWithType> | <span data-ttu-id="3584d-208">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-208">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FormatException?displayProperty=nameWithType> | <span data-ttu-id="3584d-209">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-209">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> | |
> | <xref:System.Globalization.CultureNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="3584d-210">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-210">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.SortVersion?displayProperty=nameWithType> | |
> | <xref:System.Guid?displayProperty=nameWithType> | |
> | `System.IO.Compression.ZLibException` | <span data-ttu-id="3584d-211">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-211">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DriveNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="3584d-212">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-212">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.EndOfStreamException?displayProperty=nameWithType> | <span data-ttu-id="3584d-213">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-213">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileFormatException?displayProperty=nameWithType> | <span data-ttu-id="3584d-214">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-214">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileLoadException?displayProperty=nameWithType> | <span data-ttu-id="3584d-215">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-215">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="3584d-216">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-216">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IOException?displayProperty=nameWithType> | <span data-ttu-id="3584d-217">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-217">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InternalBufferOverflowException?displayProperty=nameWithType> | <span data-ttu-id="3584d-218">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-218">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InvalidDataException?displayProperty=nameWithType> | <span data-ttu-id="3584d-219">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-219">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IsolatedStorage.IsolatedStorageException?displayProperty=nameWithType> | <span data-ttu-id="3584d-220">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-220">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.PathTooLongException?displayProperty=nameWithType> | <span data-ttu-id="3584d-221">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-221">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="3584d-222">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-222">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientExecutionStackException?displayProperty=nameWithType> | <span data-ttu-id="3584d-223">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-223">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientMemoryException?displayProperty=nameWithType> | <span data-ttu-id="3584d-224">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-224">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Int16?displayProperty=nameWithType> | |
> | <xref:System.Int32?displayProperty=nameWithType> | |
> | <xref:System.Int64?displayProperty=nameWithType> | |
> | <xref:System.IntPtr?displayProperty=nameWithType> | |
> | <xref:System.InvalidCastException?displayProperty=nameWithType> | <span data-ttu-id="3584d-225">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-225">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidOperationException?displayProperty=nameWithType> | <span data-ttu-id="3584d-226">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-226">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidProgramException?displayProperty=nameWithType> | <span data-ttu-id="3584d-227">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-227">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidTimeZoneException?displayProperty=nameWithType> | <span data-ttu-id="3584d-228">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-228">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MemberAccessException?displayProperty=nameWithType> | <span data-ttu-id="3584d-229">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-229">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MethodAccessException?displayProperty=nameWithType> | <span data-ttu-id="3584d-230">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-230">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingFieldException?displayProperty=nameWithType> | <span data-ttu-id="3584d-231">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-231">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMemberException?displayProperty=nameWithType> | <span data-ttu-id="3584d-232">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-232">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMethodException?displayProperty=nameWithType> | <span data-ttu-id="3584d-233">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-233">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MulticastNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="3584d-234">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-234">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Cookie?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieCollection?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieContainer?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieException?displayProperty=nameWithType> | <span data-ttu-id="3584d-235">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-235">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.HttpListenerException?displayProperty=nameWithType> | <span data-ttu-id="3584d-236">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-236">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpException?displayProperty=nameWithType> | <span data-ttu-id="3584d-237">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-237">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientException?displayProperty=nameWithType> | <span data-ttu-id="3584d-238">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-238">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientsException?displayProperty=nameWithType> | <span data-ttu-id="3584d-239">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-239">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.NetworkInformationException?displayProperty=nameWithType> | <span data-ttu-id="3584d-240">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-240">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.PingException?displayProperty=nameWithType> | <span data-ttu-id="3584d-241">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-241">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.ProtocolViolationException?displayProperty=nameWithType> | <span data-ttu-id="3584d-242">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-242">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Sockets.SocketException?displayProperty=nameWithType> | <span data-ttu-id="3584d-243">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-243">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebException?displayProperty=nameWithType> | <span data-ttu-id="3584d-244">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-244">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebSockets.WebSocketException?displayProperty=nameWithType> | <span data-ttu-id="3584d-245">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-245">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotFiniteNumberException?displayProperty=nameWithType> | <span data-ttu-id="3584d-246">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-246">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotImplementedException?displayProperty=nameWithType> | <span data-ttu-id="3584d-247">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-247">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="3584d-248">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-248">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NullReferenceException?displayProperty=nameWithType> | <span data-ttu-id="3584d-249">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-249">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Nullable%601?displayProperty=nameWithType> | |
> | <xref:System.Numerics.BigInteger?displayProperty=nameWithType> | |
> | <xref:System.Numerics.Complex?displayProperty=nameWithType> | |
> | <xref:System.Object?displayProperty=nameWithType> | |
> | <xref:System.ObjectDisposedException?displayProperty=nameWithType> | <span data-ttu-id="3584d-250">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-250">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OperationCanceledException?displayProperty=nameWithType> | <span data-ttu-id="3584d-251">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-251">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OutOfMemoryException?displayProperty=nameWithType> | <span data-ttu-id="3584d-252">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-252">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OverflowException?displayProperty=nameWithType> | <span data-ttu-id="3584d-253">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-253">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.PlatformNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="3584d-254">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-254">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.RankException?displayProperty=nameWithType> | <span data-ttu-id="3584d-255">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-255">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.AmbiguousMatchException?displayProperty=nameWithType> | <span data-ttu-id="3584d-256">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-256">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.CustomAttributeFormatException?displayProperty=nameWithType> | <span data-ttu-id="3584d-257">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-257">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.InvalidFilterCriteriaException?displayProperty=nameWithType> | <span data-ttu-id="3584d-258">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-258">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.ReflectionTypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="3584d-259">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-259">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="3584d-260">Serializace z rozhraní .NET Framework na .NET Core není podporována.</span><span class="sxs-lookup"><span data-stu-id="3584d-260">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.Reflection.TargetException?displayProperty=nameWithType> | <span data-ttu-id="3584d-261">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-261">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetInvocationException?displayProperty=nameWithType> | <span data-ttu-id="3584d-262">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-262">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetParameterCountException?displayProperty=nameWithType> | <span data-ttu-id="3584d-263">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-263">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingManifestResourceException?displayProperty=nameWithType> | <span data-ttu-id="3584d-264">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-264">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingSatelliteAssemblyException?displayProperty=nameWithType> | <span data-ttu-id="3584d-265">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-265">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.CompilerServices.RuntimeWrappedException?displayProperty=nameWithType> | <span data-ttu-id="3584d-266">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-266">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.COMException?displayProperty=nameWithType> | <span data-ttu-id="3584d-267">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-267">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.ExternalException?displayProperty=nameWithType> | <span data-ttu-id="3584d-268">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-268">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidComObjectException?displayProperty=nameWithType> | <span data-ttu-id="3584d-269">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-269">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidOleVariantTypeException?displayProperty=nameWithType> | <span data-ttu-id="3584d-270">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-270">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.MarshalDirectiveException?displayProperty=nameWithType> | <span data-ttu-id="3584d-271">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-271">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SEHException?displayProperty=nameWithType> | <span data-ttu-id="3584d-272">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-272">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException?displayProperty=nameWithType> | <span data-ttu-id="3584d-273">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-273">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="3584d-274">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-274">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.InvalidDataContractException?displayProperty=nameWithType> | <span data-ttu-id="3584d-275">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-275">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.SerializationException?displayProperty=nameWithType> | <span data-ttu-id="3584d-276">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-276">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.SByte?displayProperty=nameWithType> | |
> | <xref:System.Security.AccessControl.PrivilegeNotHeldException?displayProperty=nameWithType> | <span data-ttu-id="3584d-277">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-277">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.AuthenticationException?displayProperty=nameWithType> | <span data-ttu-id="3584d-278">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-278">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.InvalidCredentialException?displayProperty=nameWithType> | <span data-ttu-id="3584d-279">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-279">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicException?displayProperty=nameWithType> | <span data-ttu-id="3584d-280">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-280">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicUnexpectedOperationException?displayProperty=nameWithType> | <span data-ttu-id="3584d-281">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-281">Starting in .NET Core 2.0.4.</span></span> |
> | `System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException` | <span data-ttu-id="3584d-282">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-282">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.HostProtectionException?displayProperty=nameWithType> | <span data-ttu-id="3584d-283">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-283">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Policy.PolicyException?displayProperty=nameWithType> | <span data-ttu-id="3584d-284">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-284">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Principal.IdentityNotMappedException?displayProperty=nameWithType> | <span data-ttu-id="3584d-285">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-285">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.SecurityException?displayProperty=nameWithType> | <span data-ttu-id="3584d-286">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-286">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="3584d-287">Omezená serializační data.</span><span class="sxs-lookup"><span data-stu-id="3584d-287">Limited serialization data.</span></span> |
> | <xref:System.Security.VerificationException?displayProperty=nameWithType> | <span data-ttu-id="3584d-288">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-288">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.XmlSyntaxException?displayProperty=nameWithType> | <span data-ttu-id="3584d-289">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-289">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ServiceProcess.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="3584d-290">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-290">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Single?displayProperty=nameWithType> | |
> | <xref:System.StackOverflowException?displayProperty=nameWithType> | <span data-ttu-id="3584d-291">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-291">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.String?displayProperty=nameWithType> | |
> | <xref:System.StringComparer?displayProperty=nameWithType> | |
> | <xref:System.SystemException?displayProperty=nameWithType> | <span data-ttu-id="3584d-292">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-292">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.DecoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="3584d-293">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-293">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.EncoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="3584d-294">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-294">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.RegularExpressions.RegexMatchTimeoutException?displayProperty=nameWithType> | <span data-ttu-id="3584d-295">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-295">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.StringBuilder?displayProperty=nameWithType> | |
> | <xref:System.Threading.AbandonedMutexException?displayProperty=nameWithType> | <span data-ttu-id="3584d-296">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-296">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.BarrierPostPhaseException?displayProperty=nameWithType> | <span data-ttu-id="3584d-297">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-297">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.LockRecursionException?displayProperty=nameWithType> | <span data-ttu-id="3584d-298">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-298">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SemaphoreFullException?displayProperty=nameWithType> | <span data-ttu-id="3584d-299">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-299">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SynchronizationLockException?displayProperty=nameWithType> | <span data-ttu-id="3584d-300">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-300">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> | <span data-ttu-id="3584d-301">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-301">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskSchedulerException?displayProperty=nameWithType> | <span data-ttu-id="3584d-302">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-302">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> | <span data-ttu-id="3584d-303">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-303">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadInterruptedException?displayProperty=nameWithType> | <span data-ttu-id="3584d-304">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-304">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStartException?displayProperty=nameWithType> | <span data-ttu-id="3584d-305">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-305">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStateException?displayProperty=nameWithType> | <span data-ttu-id="3584d-306">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-306">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.WaitHandleCannotBeOpenedException?displayProperty=nameWithType> | <span data-ttu-id="3584d-307">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-307">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeSpan?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="3584d-308">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-308">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="3584d-309">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-309">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionAbortedException?displayProperty=nameWithType> | <span data-ttu-id="3584d-310">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-310">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionException?displayProperty=nameWithType> | <span data-ttu-id="3584d-311">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-311">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionInDoubtException?displayProperty=nameWithType> | <span data-ttu-id="3584d-312">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-312">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionManagerCommunicationException?displayProperty=nameWithType> | <span data-ttu-id="3584d-313">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-313">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionPromotionException?displayProperty=nameWithType> | <span data-ttu-id="3584d-314">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-314">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Tuple?displayProperty=nameWithType> | |
> | <xref:System.TypeAccessException?displayProperty=nameWithType> | <span data-ttu-id="3584d-315">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-315">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeInitializationException?displayProperty=nameWithType> | <span data-ttu-id="3584d-316">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-316">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="3584d-317">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-317">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="3584d-318">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-318">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.UInt16?displayProperty=nameWithType> | |
> | <xref:System.UInt32?displayProperty=nameWithType> | |
> | <xref:System.UInt64?displayProperty=nameWithType> | |
> | <xref:System.UIntPtr?displayProperty=nameWithType> | |
> | <xref:System.UnauthorizedAccessException?displayProperty=nameWithType> | <span data-ttu-id="3584d-319">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-319">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Uri?displayProperty=nameWithType> | |
> | <xref:System.UriFormatException?displayProperty=nameWithType> | <span data-ttu-id="3584d-320">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-320">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ValueTuple?displayProperty=nameWithType> | <span data-ttu-id="3584d-321">Nelze serializovat v rozhraní .NET Framework 4.7 a starších verzích.</span><span class="sxs-lookup"><span data-stu-id="3584d-321">Not serializable in .NET Framework 4.7 and earlier versions.</span></span> |
> | <xref:System.ValueType?displayProperty=nameWithType> | |
> | <xref:System.Version?displayProperty=nameWithType> | |
> | <xref:System.WeakReference%601?displayProperty=nameWithType> | |
> | <xref:System.WeakReference?displayProperty=nameWithType> | |
> | <xref:System.Xml.Schema.XmlSchemaException?displayProperty=nameWithType> | <span data-ttu-id="3584d-322">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-322">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaInferenceException?displayProperty=nameWithType> | <span data-ttu-id="3584d-323">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-323">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaValidationException?displayProperty=nameWithType> | <span data-ttu-id="3584d-324">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-324">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XPath.XPathException?displayProperty=nameWithType> | <span data-ttu-id="3584d-325">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-325">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XmlException?displayProperty=nameWithType> | <span data-ttu-id="3584d-326">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-326">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltCompileException?displayProperty=nameWithType> | <span data-ttu-id="3584d-327">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-327">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltException?displayProperty=nameWithType> | <span data-ttu-id="3584d-328">Počínaje rozhraním .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="3584d-328">Starting in .NET Core 2.0.4.</span></span> |

## <a name="see-also"></a><span data-ttu-id="3584d-329">Viz také</span><span class="sxs-lookup"><span data-stu-id="3584d-329">See also</span></span>

- <xref:System.Runtime.Serialization>\
<span data-ttu-id="3584d-330">Obsahuje třídy, které lze použít pro serializaci a deserializaci objektů.</span><span class="sxs-lookup"><span data-stu-id="3584d-330">Contains classes that can be used for serializing and deserializing objects.</span></span>

- <span data-ttu-id="3584d-331">[Serializace XML a SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="3584d-331">[XML and SOAP Serialization](../../../docs/standard/serialization/xml-and-soap-serialization.md)</span></span>\
<span data-ttu-id="3584d-332">Popisuje mechanismus serializace XML, který je součástí common language runtime.</span><span class="sxs-lookup"><span data-stu-id="3584d-332">Describes the XML serialization mechanism that is included with the common language runtime.</span></span>

- <span data-ttu-id="3584d-333">[Zabezpečení a serializace](../../../docs/framework/misc/security-and-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="3584d-333">[Security and Serialization](../../../docs/framework/misc/security-and-serialization.md)</span></span>\
<span data-ttu-id="3584d-334">Popisuje zabezpečené kódování zásady dodržovat při psaní kódu, který provede serializaci.</span><span class="sxs-lookup"><span data-stu-id="3584d-334">Describes the secure coding guidelines to follow when writing code that performs serialization.</span></span>

- <span data-ttu-id="3584d-335">[Vzdálené komunikace v rozhraní .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3584d-335">[.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span></span>\
<span data-ttu-id="3584d-336">Popisuje různé metody spuštění v rozhraní .NET Framework pro vzdálenou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="3584d-336">Describes the various methods Starting in .NET Framework for remote communications.</span></span>

- <span data-ttu-id="3584d-337">[Webové služby XML vytvořené pomocí ASP.NET a klientů webových služeb XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3584d-337">[XML Web Services Created Using ASP.NET and XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>\
<span data-ttu-id="3584d-338">Články, které popisují a vysvětlují, jak programovat webové služby XML vytvořené pomocí ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3584d-338">Articles that describe and explain how to program XML Web services created using ASP.NET.</span></span>
