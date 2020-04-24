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
# <a name="binary-serialization"></a><span data-ttu-id="ba833-102">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="ba833-102">Binary serialization</span></span>

<span data-ttu-id="ba833-103">Serializace může být definován jako proces ukládání stavu objektu do úložiště média.</span><span class="sxs-lookup"><span data-stu-id="ba833-103">Serialization can be defined as the process of storing the state of an object to a storage medium.</span></span> <span data-ttu-id="ba833-104">Během tohoto procesu se veřejné a soukromé pole objektu a název třídy, včetně sestavení obsahující dané třídy, jsou převedeny do datového proudu bajtů, které jsou následně zapsána do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="ba833-104">During this process, the public and private fields of the object and the name of the class, including the assembly containing the class, are converted to a stream of bytes, which is then written to a data stream.</span></span> <span data-ttu-id="ba833-105">Při objektu je následně deserializovat, je vytvořena přesné klon původní objekt.</span><span class="sxs-lookup"><span data-stu-id="ba833-105">When the object is subsequently deserialized, an exact clone of the original object is created.</span></span>

<span data-ttu-id="ba833-106">Při provádění mechanismus serializace v prostředí objektově orientované, je třeba vytvořit počet kompromisy mezi snadnost použití a flexibilitu.</span><span class="sxs-lookup"><span data-stu-id="ba833-106">When implementing a serialization mechanism in an object-oriented environment, you have to make a number of tradeoffs between ease of use and flexibility.</span></span> <span data-ttu-id="ba833-107">Proces můžete automatizované do značné míry, za předpokladu, že budete mít dostatečné kontrolu nad procesem.</span><span class="sxs-lookup"><span data-stu-id="ba833-107">The process can be automated to a large extent, provided you are given sufficient control over the process.</span></span> <span data-ttu-id="ba833-108">Například může nastat situace, kde jednoduché binární serializace není dostatečné, nebo mohou existovat konkrétní důvod, proč se rozhodnout, která pole v třídě muset být serializován.</span><span class="sxs-lookup"><span data-stu-id="ba833-108">For example, situations may arise where simple binary serialization is not sufficient, or there might be a specific reason to decide which fields in a class need to be serialized.</span></span> <span data-ttu-id="ba833-109">Následující části prozkoumají robustní mechanizmus serializace, který je součástí .NET, a zvýrazní celou řadu důležitých funkcí, které vám umožní přizpůsobit proces tak, aby vyhovoval vašim potřebám.</span><span class="sxs-lookup"><span data-stu-id="ba833-109">The following sections examine the robust serialization mechanism provided with .NET and highlight a number of important features that allow you to customize the process to meet your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="ba833-110">Stav UTF-8 nebo UTF-7 objekt není zachováváno, je-li objekt je serializaci a deserializaci pomocí různých verzí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ba833-110">The state of a UTF-8 or UTF-7 encoded object is not preserved if the object is serialized and deserialized using different .NET Framework versions.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="ba833-111">Binární serializace umožňuje upravovat soukromé členy uvnitř objektu, a proto mění stav.</span><span class="sxs-lookup"><span data-stu-id="ba833-111">Binary serialization allows modifying private members inside an object and therefore changing the state of it.</span></span> <span data-ttu-id="ba833-112">Z tohoto důvodu jsou doporučeny jiné architektury serializace <xref:System.Text.Json?displayProperty=fullName>, jako například, které fungují na veřejné ploše rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="ba833-112">Because of this, other serialization frameworks, like <xref:System.Text.Json?displayProperty=fullName>, that operate on the public API surface are recommended.</span></span>

## <a name="net-core"></a><span data-ttu-id="ba833-113">.NET Core</span><span class="sxs-lookup"><span data-stu-id="ba833-113">.NET Core</span></span>

<span data-ttu-id="ba833-114">.NET Core podporuje binární serializaci pro podmnožinu typů.</span><span class="sxs-lookup"><span data-stu-id="ba833-114">.NET Core supports binary serialization for a subset of types.</span></span> <span data-ttu-id="ba833-115">Seznam podporovaných typů můžete zobrazit v níže uvedené části [serializovatelný typy](#serializable-types) .</span><span class="sxs-lookup"><span data-stu-id="ba833-115">You can see the list of supported types in the [Serializable types](#serializable-types) section that follows.</span></span> <span data-ttu-id="ba833-116">U uvedených typů je zaručena serializace mezi .NET Framework 4.5.1 a novějšími verzemi a mezi .NET Core 2,0 a novějšími verzemi.</span><span class="sxs-lookup"><span data-stu-id="ba833-116">The listed types are guaranteed to be serializable between .NET Framework 4.5.1 and later versions and between .NET Core 2.0 and later versions.</span></span> <span data-ttu-id="ba833-117">Jiné implementace rozhraní .NET, jako je například mono, nejsou oficiálně podporovány, ale měly by také fungovat.</span><span class="sxs-lookup"><span data-stu-id="ba833-117">Other .NET implementations, such as Mono, aren't officially supported but should also work.</span></span>

### <a name="serializable-types"></a><span data-ttu-id="ba833-118">Serializovatelné typy</span><span class="sxs-lookup"><span data-stu-id="ba833-118">Serializable types</span></span>

> [!div class="mx-tdCol2BreakAll"]
> | <span data-ttu-id="ba833-119">Typ</span><span class="sxs-lookup"><span data-stu-id="ba833-119">Type</span></span> | <span data-ttu-id="ba833-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ba833-120">Notes</span></span> |
> | - | - |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderException?displayProperty=nameWithType> | <span data-ttu-id="ba833-121">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-121">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderInternalCompilerException?displayProperty=nameWithType> | <span data-ttu-id="ba833-122">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-122">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AccessViolationException?displayProperty=nameWithType> | <span data-ttu-id="ba833-123">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-123">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AggregateException?displayProperty=nameWithType> | <span data-ttu-id="ba833-124">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-124">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="ba833-125">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-125">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ApplicationException?displayProperty=nameWithType> | <span data-ttu-id="ba833-126">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-126">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentException?displayProperty=nameWithType> | <span data-ttu-id="ba833-127">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-127">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentNullException?displayProperty=nameWithType> | <span data-ttu-id="ba833-128">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-128">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="ba833-129">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-129">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArithmeticException?displayProperty=nameWithType> | <span data-ttu-id="ba833-130">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-130">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Array?displayProperty=nameWithType> | |
> | <xref:System.ArraySegment%601?displayProperty=nameWithType> | |
> | <xref:System.ArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="ba833-131">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-131">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Attribute?displayProperty=nameWithType> | |
> | <xref:System.BadImageFormatException?displayProperty=nameWithType> | <span data-ttu-id="ba833-132">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-132">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Boolean?displayProperty=nameWithType> | |
> | <xref:System.Byte?displayProperty=nameWithType> | |
> | <xref:System.CannotUnloadAppDomainException?displayProperty=nameWithType> | <span data-ttu-id="ba833-133">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-133">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Char?displayProperty=nameWithType> | |
> | <xref:System.Collections.ArrayList?displayProperty=nameWithType> | |
> | <xref:System.Collections.BitArray?displayProperty=nameWithType> | |
> | <xref:System.Collections.Comparer?displayProperty=nameWithType> | |
> | <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ba833-134">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-134">Starting in .NET Core 2.0.4.</span></span> |
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
> | `System.Collections.Generic.NonRandomizedStringEqualityComparer` | <span data-ttu-id="ba833-135">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-135">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType> | |
> | <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType> | <span data-ttu-id="ba833-136">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-136">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Design.CheckoutException?displayProperty=nameWithType> | <span data-ttu-id="ba833-137">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-137">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidAsynchronousStateException?displayProperty=nameWithType> | <span data-ttu-id="ba833-138">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-138">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=nameWithType> | <span data-ttu-id="ba833-139">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-139">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.LicenseException?displayProperty=nameWithType> | <span data-ttu-id="ba833-140">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-140">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="ba833-141">Serializace z .NET Framework do .NET Core není podporována.</span><span class="sxs-lookup"><span data-stu-id="ba833-141">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.ComponentModel.WarningException?displayProperty=nameWithType> | <span data-ttu-id="ba833-142">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-142">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Win32Exception?displayProperty=nameWithType> | <span data-ttu-id="ba833-143">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-143">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType> | <span data-ttu-id="ba833-144">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-144">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationException?displayProperty=nameWithType> | <span data-ttu-id="ba833-145">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-145">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.Provider.ProviderException?displayProperty=nameWithType> | <span data-ttu-id="ba833-146">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-146">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyIsReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="ba833-147">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-147">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ba833-148">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-148">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyWrongTypeException?displayProperty=nameWithType> | <span data-ttu-id="ba833-149">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-149">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ContextMarshalException?displayProperty=nameWithType> | <span data-ttu-id="ba833-150">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-150">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DBNull?displayProperty=nameWithType> | <span data-ttu-id="ba833-151">Počínaje .NET Core 2.0.2 a novějšími verzemi.</span><span class="sxs-lookup"><span data-stu-id="ba833-151">Starting in .NET Core 2.0.2 and later versions.</span></span> |
> | <xref:System.Data.Common.DbException?displayProperty=nameWithType> | <span data-ttu-id="ba833-152">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-152">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.ConstraintException?displayProperty=nameWithType> | <span data-ttu-id="ba833-153">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-153">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DBConcurrencyException?displayProperty=nameWithType> | <span data-ttu-id="ba833-154">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-154">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataException?displayProperty=nameWithType> | <span data-ttu-id="ba833-155">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-155">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataSet?displayProperty=nameWithType> | |
> | <xref:System.Data.DataTable?displayProperty=nameWithType> | <span data-ttu-id="ba833-156">Pokud nastavíte `RemotingFormat` `SerializationFormat.Binary`, můžete ho vyměnit jenom pomocí .NET Core 2,1 a novějších verzí.</span><span class="sxs-lookup"><span data-stu-id="ba833-156">If you set `RemotingFormat` to `SerializationFormat.Binary`, it can only be exchanged with .NET Core 2.1 and later versions.</span></span> |
> | <xref:System.Data.DeletedRowInaccessibleException?displayProperty=nameWithType> | <span data-ttu-id="ba833-157">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-157">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DuplicateNameException?displayProperty=nameWithType> | <span data-ttu-id="ba833-158">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-158">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.EvaluateException?displayProperty=nameWithType> | <span data-ttu-id="ba833-159">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-159">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InRowChangingEventException?displayProperty=nameWithType> | <span data-ttu-id="ba833-160">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-160">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidConstraintException?displayProperty=nameWithType> | <span data-ttu-id="ba833-161">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-161">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidExpressionException?displayProperty=nameWithType> | <span data-ttu-id="ba833-162">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-162">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.MissingPrimaryKeyException?displayProperty=nameWithType> | <span data-ttu-id="ba833-163">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-163">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.NoNullAllowedException?displayProperty=nameWithType> | <span data-ttu-id="ba833-164">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-164">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.Odbc.OdbcException?displayProperty=nameWithType> | <span data-ttu-id="ba833-165">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-165">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.OperationAbortedException?displayProperty=nameWithType> | <span data-ttu-id="ba833-166">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-166">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.PropertyCollection?displayProperty=nameWithType> | |
> | <xref:System.Data.ReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="ba833-167">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-167">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.RowNotInTableException?displayProperty=nameWithType> | <span data-ttu-id="ba833-168">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-168">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlClient.SqlException?displayProperty=nameWithType> | <span data-ttu-id="ba833-169">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-169">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="ba833-170">Serializace z .NET Framework do .NET Core není podporována.</span><span class="sxs-lookup"><span data-stu-id="ba833-170">Serialization from .NET Framework to .NET Core is not supported</span></span> |
> | <xref:System.Data.SqlTypes.SqlAlreadyFilledException?displayProperty=nameWithType> | <span data-ttu-id="ba833-171">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-171">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlNotFilledException?displayProperty=nameWithType> | <span data-ttu-id="ba833-172">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-172">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlNullValueException?displayProperty=nameWithType> | <span data-ttu-id="ba833-173">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-173">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlTruncateException?displayProperty=nameWithType> | <span data-ttu-id="ba833-174">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-174">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlTypeException?displayProperty=nameWithType> | <span data-ttu-id="ba833-175">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-175">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.StrongTypingException?displayProperty=nameWithType> | <span data-ttu-id="ba833-176">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-176">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SyntaxErrorException?displayProperty=nameWithType> | <span data-ttu-id="ba833-177">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-177">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.VersionNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ba833-178">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-178">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DataMisalignedException?displayProperty=nameWithType> | <span data-ttu-id="ba833-179">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-179">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DateTime?displayProperty=nameWithType> | |
> | <xref:System.DateTimeOffset?displayProperty=nameWithType> | |
> | <xref:System.Decimal?displayProperty=nameWithType> | |
> | `System.Diagnostics.Contracts.ContractException` | <span data-ttu-id="ba833-180">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-180">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Diagnostics.Tracing.EventSourceException?displayProperty=nameWithType> | <span data-ttu-id="ba833-181">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-181">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ba833-182">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-182">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.MultipleMatchesException?displayProperty=nameWithType> | <span data-ttu-id="ba833-183">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-183">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.NoMatchingPrincipalException?displayProperty=nameWithType> | <span data-ttu-id="ba833-184">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-184">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PasswordException?displayProperty=nameWithType> | <span data-ttu-id="ba833-185">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-185">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalException?displayProperty=nameWithType> | <span data-ttu-id="ba833-186">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-186">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalExistsException?displayProperty=nameWithType> | <span data-ttu-id="ba833-187">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-187">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalOperationException?displayProperty=nameWithType> | <span data-ttu-id="ba833-188">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-188">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalServerDownException?displayProperty=nameWithType> | <span data-ttu-id="ba833-189">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-189">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectExistsException?displayProperty=nameWithType> | <span data-ttu-id="ba833-190">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-190">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ba833-191">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-191">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="ba833-192">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-192">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryServerDownException?displayProperty=nameWithType> | <span data-ttu-id="ba833-193">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-193">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ForestTrustCollisionException?displayProperty=nameWithType> | <span data-ttu-id="ba833-194">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-194">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.SyncFromAllServersOperationException?displayProperty=nameWithType> | <span data-ttu-id="ba833-195">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-195">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.DirectoryServicesCOMException?displayProperty=nameWithType> | <span data-ttu-id="ba833-196">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-196">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.BerConversionException?displayProperty=nameWithType> | <span data-ttu-id="ba833-197">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-197">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryException?displayProperty=nameWithType> | <span data-ttu-id="ba833-198">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-198">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="ba833-199">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-199">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.LdapException?displayProperty=nameWithType> | <span data-ttu-id="ba833-200">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-200">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.TlsOperationException?displayProperty=nameWithType> | <span data-ttu-id="ba833-201">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-201">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DivideByZeroException?displayProperty=nameWithType> | <span data-ttu-id="ba833-202">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-202">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DllNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ba833-203">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-203">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Double?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Color?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Point?displayProperty=nameWithType> | |
> | <xref:System.Drawing.PointF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Rectangle?displayProperty=nameWithType> | |
> | <xref:System.Drawing.RectangleF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Size?displayProperty=nameWithType> | |
> | <xref:System.Drawing.SizeF?displayProperty=nameWithType> | |
> | <xref:System.DuplicateWaitObjectException?displayProperty=nameWithType> | <span data-ttu-id="ba833-204">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-204">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.EntryPointNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ba833-205">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-205">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Enum?displayProperty=nameWithType> | |
> | <xref:System.EventArgs?displayProperty=nameWithType> | <span data-ttu-id="ba833-206">Začíná v .NET Core 2.0.6.</span><span class="sxs-lookup"><span data-stu-id="ba833-206">Starting in .NET Core 2.0.6.</span></span> |
> | <xref:System.Exception?displayProperty=nameWithType> | |
> | <xref:System.ExecutionEngineException?displayProperty=nameWithType> | <span data-ttu-id="ba833-207">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-207">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FieldAccessException?displayProperty=nameWithType> | <span data-ttu-id="ba833-208">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-208">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FormatException?displayProperty=nameWithType> | <span data-ttu-id="ba833-209">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-209">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> | |
> | <xref:System.Globalization.CultureNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ba833-210">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-210">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.SortVersion?displayProperty=nameWithType> | |
> | <xref:System.Guid?displayProperty=nameWithType> | |
> | `System.IO.Compression.ZLibException` | <span data-ttu-id="ba833-211">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-211">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DriveNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ba833-212">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-212">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.EndOfStreamException?displayProperty=nameWithType> | <span data-ttu-id="ba833-213">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-213">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileFormatException?displayProperty=nameWithType> | <span data-ttu-id="ba833-214">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-214">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileLoadException?displayProperty=nameWithType> | <span data-ttu-id="ba833-215">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-215">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ba833-216">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-216">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IOException?displayProperty=nameWithType> | <span data-ttu-id="ba833-217">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-217">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InternalBufferOverflowException?displayProperty=nameWithType> | <span data-ttu-id="ba833-218">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-218">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InvalidDataException?displayProperty=nameWithType> | <span data-ttu-id="ba833-219">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-219">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IsolatedStorage.IsolatedStorageException?displayProperty=nameWithType> | <span data-ttu-id="ba833-220">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-220">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.PathTooLongException?displayProperty=nameWithType> | <span data-ttu-id="ba833-221">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-221">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="ba833-222">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-222">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientExecutionStackException?displayProperty=nameWithType> | <span data-ttu-id="ba833-223">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-223">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientMemoryException?displayProperty=nameWithType> | <span data-ttu-id="ba833-224">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-224">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Int16?displayProperty=nameWithType> | |
> | <xref:System.Int32?displayProperty=nameWithType> | |
> | <xref:System.Int64?displayProperty=nameWithType> | |
> | <xref:System.IntPtr?displayProperty=nameWithType> | |
> | <xref:System.InvalidCastException?displayProperty=nameWithType> | <span data-ttu-id="ba833-225">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-225">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidOperationException?displayProperty=nameWithType> | <span data-ttu-id="ba833-226">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-226">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidProgramException?displayProperty=nameWithType> | <span data-ttu-id="ba833-227">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-227">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidTimeZoneException?displayProperty=nameWithType> | <span data-ttu-id="ba833-228">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-228">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MemberAccessException?displayProperty=nameWithType> | <span data-ttu-id="ba833-229">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-229">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MethodAccessException?displayProperty=nameWithType> | <span data-ttu-id="ba833-230">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-230">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingFieldException?displayProperty=nameWithType> | <span data-ttu-id="ba833-231">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-231">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMemberException?displayProperty=nameWithType> | <span data-ttu-id="ba833-232">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-232">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMethodException?displayProperty=nameWithType> | <span data-ttu-id="ba833-233">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-233">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MulticastNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="ba833-234">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-234">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Cookie?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieCollection?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieContainer?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieException?displayProperty=nameWithType> | <span data-ttu-id="ba833-235">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-235">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.HttpListenerException?displayProperty=nameWithType> | <span data-ttu-id="ba833-236">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-236">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpException?displayProperty=nameWithType> | <span data-ttu-id="ba833-237">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-237">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientException?displayProperty=nameWithType> | <span data-ttu-id="ba833-238">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-238">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientsException?displayProperty=nameWithType> | <span data-ttu-id="ba833-239">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-239">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.NetworkInformationException?displayProperty=nameWithType> | <span data-ttu-id="ba833-240">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-240">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.PingException?displayProperty=nameWithType> | <span data-ttu-id="ba833-241">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-241">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.ProtocolViolationException?displayProperty=nameWithType> | <span data-ttu-id="ba833-242">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-242">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Sockets.SocketException?displayProperty=nameWithType> | <span data-ttu-id="ba833-243">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-243">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebException?displayProperty=nameWithType> | <span data-ttu-id="ba833-244">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-244">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebSockets.WebSocketException?displayProperty=nameWithType> | <span data-ttu-id="ba833-245">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-245">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotFiniteNumberException?displayProperty=nameWithType> | <span data-ttu-id="ba833-246">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-246">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotImplementedException?displayProperty=nameWithType> | <span data-ttu-id="ba833-247">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-247">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="ba833-248">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-248">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NullReferenceException?displayProperty=nameWithType> | <span data-ttu-id="ba833-249">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-249">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Nullable%601?displayProperty=nameWithType> | |
> | <xref:System.Numerics.BigInteger?displayProperty=nameWithType> | |
> | <xref:System.Numerics.Complex?displayProperty=nameWithType> | |
> | <xref:System.Object?displayProperty=nameWithType> | |
> | <xref:System.ObjectDisposedException?displayProperty=nameWithType> | <span data-ttu-id="ba833-250">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-250">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OperationCanceledException?displayProperty=nameWithType> | <span data-ttu-id="ba833-251">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-251">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OutOfMemoryException?displayProperty=nameWithType> | <span data-ttu-id="ba833-252">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-252">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OverflowException?displayProperty=nameWithType> | <span data-ttu-id="ba833-253">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-253">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.PlatformNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="ba833-254">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-254">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.RankException?displayProperty=nameWithType> | <span data-ttu-id="ba833-255">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-255">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.AmbiguousMatchException?displayProperty=nameWithType> | <span data-ttu-id="ba833-256">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-256">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.CustomAttributeFormatException?displayProperty=nameWithType> | <span data-ttu-id="ba833-257">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-257">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.InvalidFilterCriteriaException?displayProperty=nameWithType> | <span data-ttu-id="ba833-258">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-258">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.ReflectionTypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="ba833-259">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-259">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="ba833-260">Serializace z .NET Framework do .NET Core není podporována.</span><span class="sxs-lookup"><span data-stu-id="ba833-260">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.Reflection.TargetException?displayProperty=nameWithType> | <span data-ttu-id="ba833-261">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-261">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetInvocationException?displayProperty=nameWithType> | <span data-ttu-id="ba833-262">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-262">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetParameterCountException?displayProperty=nameWithType> | <span data-ttu-id="ba833-263">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-263">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingManifestResourceException?displayProperty=nameWithType> | <span data-ttu-id="ba833-264">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-264">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingSatelliteAssemblyException?displayProperty=nameWithType> | <span data-ttu-id="ba833-265">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-265">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.CompilerServices.RuntimeWrappedException?displayProperty=nameWithType> | <span data-ttu-id="ba833-266">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-266">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.COMException?displayProperty=nameWithType> | <span data-ttu-id="ba833-267">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-267">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.ExternalException?displayProperty=nameWithType> | <span data-ttu-id="ba833-268">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-268">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidComObjectException?displayProperty=nameWithType> | <span data-ttu-id="ba833-269">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-269">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidOleVariantTypeException?displayProperty=nameWithType> | <span data-ttu-id="ba833-270">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-270">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.MarshalDirectiveException?displayProperty=nameWithType> | <span data-ttu-id="ba833-271">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-271">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SEHException?displayProperty=nameWithType> | <span data-ttu-id="ba833-272">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-272">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException?displayProperty=nameWithType> | <span data-ttu-id="ba833-273">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-273">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="ba833-274">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-274">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.InvalidDataContractException?displayProperty=nameWithType> | <span data-ttu-id="ba833-275">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-275">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.SerializationException?displayProperty=nameWithType> | <span data-ttu-id="ba833-276">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-276">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.SByte?displayProperty=nameWithType> | |
> | <xref:System.Security.AccessControl.PrivilegeNotHeldException?displayProperty=nameWithType> | <span data-ttu-id="ba833-277">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-277">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.AuthenticationException?displayProperty=nameWithType> | <span data-ttu-id="ba833-278">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-278">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.InvalidCredentialException?displayProperty=nameWithType> | <span data-ttu-id="ba833-279">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-279">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicException?displayProperty=nameWithType> | <span data-ttu-id="ba833-280">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-280">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicUnexpectedOperationException?displayProperty=nameWithType> | <span data-ttu-id="ba833-281">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-281">Starting in .NET Core 2.0.4.</span></span> |
> | `System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException` | <span data-ttu-id="ba833-282">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-282">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.HostProtectionException?displayProperty=nameWithType> | <span data-ttu-id="ba833-283">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-283">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Policy.PolicyException?displayProperty=nameWithType> | <span data-ttu-id="ba833-284">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-284">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Principal.IdentityNotMappedException?displayProperty=nameWithType> | <span data-ttu-id="ba833-285">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-285">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.SecurityException?displayProperty=nameWithType> | <span data-ttu-id="ba833-286">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-286">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="ba833-287">Omezená data serializace.</span><span class="sxs-lookup"><span data-stu-id="ba833-287">Limited serialization data.</span></span> |
> | <xref:System.Security.VerificationException?displayProperty=nameWithType> | <span data-ttu-id="ba833-288">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-288">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.XmlSyntaxException?displayProperty=nameWithType> | <span data-ttu-id="ba833-289">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-289">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ServiceProcess.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="ba833-290">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-290">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Single?displayProperty=nameWithType> | |
> | <xref:System.StackOverflowException?displayProperty=nameWithType> | <span data-ttu-id="ba833-291">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-291">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.String?displayProperty=nameWithType> | |
> | <xref:System.StringComparer?displayProperty=nameWithType> | |
> | <xref:System.SystemException?displayProperty=nameWithType> | <span data-ttu-id="ba833-292">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-292">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.DecoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="ba833-293">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-293">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.EncoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="ba833-294">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-294">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.RegularExpressions.RegexMatchTimeoutException?displayProperty=nameWithType> | <span data-ttu-id="ba833-295">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-295">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.StringBuilder?displayProperty=nameWithType> | |
> | <xref:System.Threading.AbandonedMutexException?displayProperty=nameWithType> | <span data-ttu-id="ba833-296">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-296">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.BarrierPostPhaseException?displayProperty=nameWithType> | <span data-ttu-id="ba833-297">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-297">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.LockRecursionException?displayProperty=nameWithType> | <span data-ttu-id="ba833-298">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-298">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SemaphoreFullException?displayProperty=nameWithType> | <span data-ttu-id="ba833-299">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-299">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SynchronizationLockException?displayProperty=nameWithType> | <span data-ttu-id="ba833-300">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-300">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> | <span data-ttu-id="ba833-301">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-301">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskSchedulerException?displayProperty=nameWithType> | <span data-ttu-id="ba833-302">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-302">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> | <span data-ttu-id="ba833-303">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-303">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadInterruptedException?displayProperty=nameWithType> | <span data-ttu-id="ba833-304">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-304">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStartException?displayProperty=nameWithType> | <span data-ttu-id="ba833-305">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-305">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStateException?displayProperty=nameWithType> | <span data-ttu-id="ba833-306">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-306">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.WaitHandleCannotBeOpenedException?displayProperty=nameWithType> | <span data-ttu-id="ba833-307">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-307">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeSpan?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="ba833-308">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-308">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="ba833-309">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-309">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionAbortedException?displayProperty=nameWithType> | <span data-ttu-id="ba833-310">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-310">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionException?displayProperty=nameWithType> | <span data-ttu-id="ba833-311">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-311">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionInDoubtException?displayProperty=nameWithType> | <span data-ttu-id="ba833-312">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-312">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionManagerCommunicationException?displayProperty=nameWithType> | <span data-ttu-id="ba833-313">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-313">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionPromotionException?displayProperty=nameWithType> | <span data-ttu-id="ba833-314">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-314">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Tuple?displayProperty=nameWithType> | |
> | <xref:System.TypeAccessException?displayProperty=nameWithType> | <span data-ttu-id="ba833-315">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-315">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeInitializationException?displayProperty=nameWithType> | <span data-ttu-id="ba833-316">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-316">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="ba833-317">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-317">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="ba833-318">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-318">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.UInt16?displayProperty=nameWithType> | |
> | <xref:System.UInt32?displayProperty=nameWithType> | |
> | <xref:System.UInt64?displayProperty=nameWithType> | |
> | <xref:System.UIntPtr?displayProperty=nameWithType> | |
> | <xref:System.UnauthorizedAccessException?displayProperty=nameWithType> | <span data-ttu-id="ba833-319">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-319">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Uri?displayProperty=nameWithType> | |
> | <xref:System.UriFormatException?displayProperty=nameWithType> | <span data-ttu-id="ba833-320">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-320">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ValueTuple?displayProperty=nameWithType> | <span data-ttu-id="ba833-321">Nelze serializovat v .NET Framework 4,7 a dřívějších verzích.</span><span class="sxs-lookup"><span data-stu-id="ba833-321">Not serializable in .NET Framework 4.7 and earlier versions.</span></span> |
> | <xref:System.ValueType?displayProperty=nameWithType> | |
> | <xref:System.Version?displayProperty=nameWithType> | |
> | <xref:System.WeakReference%601?displayProperty=nameWithType> | |
> | <xref:System.WeakReference?displayProperty=nameWithType> | |
> | <xref:System.Xml.Schema.XmlSchemaException?displayProperty=nameWithType> | <span data-ttu-id="ba833-322">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-322">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaInferenceException?displayProperty=nameWithType> | <span data-ttu-id="ba833-323">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-323">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaValidationException?displayProperty=nameWithType> | <span data-ttu-id="ba833-324">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-324">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XPath.XPathException?displayProperty=nameWithType> | <span data-ttu-id="ba833-325">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-325">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XmlException?displayProperty=nameWithType> | <span data-ttu-id="ba833-326">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-326">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltCompileException?displayProperty=nameWithType> | <span data-ttu-id="ba833-327">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-327">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltException?displayProperty=nameWithType> | <span data-ttu-id="ba833-328">Začíná v .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="ba833-328">Starting in .NET Core 2.0.4.</span></span> |

## <a name="see-also"></a><span data-ttu-id="ba833-329">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba833-329">See also</span></span>

- <xref:System.Runtime.Serialization>\
<span data-ttu-id="ba833-330">Obsahuje třídy, které lze použít pro serializaci a deserializaci objektů.</span><span class="sxs-lookup"><span data-stu-id="ba833-330">Contains classes that can be used for serializing and deserializing objects.</span></span>

- <span data-ttu-id="ba833-331">[Serializace XML a SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="ba833-331">[XML and SOAP Serialization](../../../docs/standard/serialization/xml-and-soap-serialization.md)</span></span>\
<span data-ttu-id="ba833-332">Popisuje mechanismus serializace XML, který je součástí common language runtime.</span><span class="sxs-lookup"><span data-stu-id="ba833-332">Describes the XML serialization mechanism that is included with the common language runtime.</span></span>

- <span data-ttu-id="ba833-333">[Zabezpečení a serializace](../../../docs/framework/misc/security-and-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="ba833-333">[Security and Serialization](../../../docs/framework/misc/security-and-serialization.md)</span></span>\
<span data-ttu-id="ba833-334">Popisuje zabezpečené kódování zásady dodržovat při psaní kódu, který provede serializaci.</span><span class="sxs-lookup"><span data-stu-id="ba833-334">Describes the secure coding guidelines to follow when writing code that performs serialization.</span></span>

- <span data-ttu-id="ba833-335">[Vzdálená komunikace .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ba833-335">[.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span></span>\
<span data-ttu-id="ba833-336">V této části najdete popis různých metod, které se spouští v .NET Framework pro vzdálenou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="ba833-336">Describes the various methods Starting in .NET Framework for remote communications.</span></span>

- <span data-ttu-id="ba833-337">[Webové služby XML vytvořené pomocí ASP.NET a klientů webové služby XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ba833-337">[XML Web Services Created Using ASP.NET and XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>\
<span data-ttu-id="ba833-338">Články, které popisují a vysvětlují, jak programovat webové služby XML pomocí ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ba833-338">Articles that describe and explain how to program XML Web services created using ASP.NET.</span></span>
