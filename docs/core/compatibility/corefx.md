---
title: Přerušující změny knihovny základních tříd
description: Obsahuje seznam nejnovějších změn v základních knihovnách .NET.
ms.date: 07/27/2020
ms.openlocfilehash: d474d5547245e57206d669531b74b5be31c98ca0
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556322"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="f466d-103">Základní knihovny .NET – přerušující změny</span><span class="sxs-lookup"><span data-stu-id="f466d-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="f466d-104">Základní knihovny .NET poskytují primitivní a další obecné typy používané .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f466d-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="f466d-105">Na této stránce jsou popsány následující přerušující se změny:</span><span class="sxs-lookup"><span data-stu-id="f466d-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="f466d-106">Zásadní změna</span><span class="sxs-lookup"><span data-stu-id="f466d-106">Breaking change</span></span> | <span data-ttu-id="f466d-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="f466d-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="f466d-108">PrincipalPermissionAttribute je zastaralá jako chyba.</span><span class="sxs-lookup"><span data-stu-id="f466d-108">PrincipalPermissionAttribute is obsolete as error</span></span>](#principalpermissionattribute-is-obsolete-as-error) | <span data-ttu-id="f466d-109">5.0</span><span class="sxs-lookup"><span data-stu-id="f466d-109">5.0</span></span> |
| [<span data-ttu-id="f466d-110">Metody serializace BinaryFormatter jsou zastaralé a zakázané v aplikacích ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f466d-110">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | <span data-ttu-id="f466d-111">5.0</span><span class="sxs-lookup"><span data-stu-id="f466d-111">5.0</span></span> |
| [<span data-ttu-id="f466d-112">Cesty kódu UTF-7 jsou zastaralé.</span><span class="sxs-lookup"><span data-stu-id="f466d-112">UTF-7 code paths are obsolete</span></span>](#utf-7-code-paths-are-obsolete) | <span data-ttu-id="f466d-113">5.0</span><span class="sxs-lookup"><span data-stu-id="f466d-113">5.0</span></span> |
| [<span data-ttu-id="f466d-114">Vector \<T> vždy vyvolá NotSupportedException pro nepodporované typy</span><span class="sxs-lookup"><span data-stu-id="f466d-114">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="f466d-115">5.0</span><span class="sxs-lookup"><span data-stu-id="f466d-115">5.0</span></span> |
| [<span data-ttu-id="f466d-116">Výchozí ActivityIdFormat je W3C.</span><span class="sxs-lookup"><span data-stu-id="f466d-116">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="f466d-117">5.0</span><span class="sxs-lookup"><span data-stu-id="f466d-117">5.0</span></span> |
| [<span data-ttu-id="f466d-118">Změna chování pro Vector2. lerp a Vector4. lerp</span><span class="sxs-lookup"><span data-stu-id="f466d-118">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="f466d-119">5.0</span><span class="sxs-lookup"><span data-stu-id="f466d-119">5.0</span></span> |
| [<span data-ttu-id="f466d-120">Metody SSE a SSE2 CompareGreaterThan správně zpracovávají vstupy NaN.</span><span class="sxs-lookup"><span data-stu-id="f466d-120">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="f466d-121">5.0</span><span class="sxs-lookup"><span data-stu-id="f466d-121">5.0</span></span> |
| [<span data-ttu-id="f466d-122">Sada CounterSet. provedení operace CreateCounterSetInstance nyní vyvolá chybu InvalidOperationException, pokud již instance existuje.</span><span class="sxs-lookup"><span data-stu-id="f466d-122">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="f466d-123">5.0</span><span class="sxs-lookup"><span data-stu-id="f466d-123">5.0</span></span> |
| [<span data-ttu-id="f466d-124">Balíček Microsoft. DotNet. PlatformAbstractions se odebral.</span><span class="sxs-lookup"><span data-stu-id="f466d-124">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="f466d-125">5.0</span><span class="sxs-lookup"><span data-stu-id="f466d-125">5.0</span></span> |
| [<span data-ttu-id="f466d-126">Rozhraní API, která verze sestav nyní hlásí produkt a nikoli verzi souboru</span><span class="sxs-lookup"><span data-stu-id="f466d-126">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="f466d-127">3.0</span><span class="sxs-lookup"><span data-stu-id="f466d-127">3.0</span></span> |
| [<span data-ttu-id="f466d-128">Vlastní instance EncoderFallbackBuffer se nemůžou vrátit rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="f466d-128">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="f466d-129">3.0</span><span class="sxs-lookup"><span data-stu-id="f466d-129">3.0</span></span> |
| [<span data-ttu-id="f466d-130">Změny chování při formátování a analýze plovoucí desetinné čárky</span><span class="sxs-lookup"><span data-stu-id="f466d-130">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="f466d-131">3.0</span><span class="sxs-lookup"><span data-stu-id="f466d-131">3.0</span></span> |
| [<span data-ttu-id="f466d-132">Operace analýzy s plovoucí desetinnou čárkou již nejsou úspěšné nebo vyvolávají výjimku OverflowException</span><span class="sxs-lookup"><span data-stu-id="f466d-132">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="f466d-133">3.0</span><span class="sxs-lookup"><span data-stu-id="f466d-133">3.0</span></span> |
| [<span data-ttu-id="f466d-134">InvalidAsynchronousStateException – přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="f466d-134">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="f466d-135">3.0</span><span class="sxs-lookup"><span data-stu-id="f466d-135">3.0</span></span> |
| [<span data-ttu-id="f466d-136">Výměna chybně formátovaných sekvencí UTF-8 se řídí pokyny pro kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="f466d-136">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="f466d-137">3.0</span><span class="sxs-lookup"><span data-stu-id="f466d-137">3.0</span></span> |
| [<span data-ttu-id="f466d-138">TypeDescriptionProviderAttribute přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="f466d-138">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="f466d-139">3.0</span><span class="sxs-lookup"><span data-stu-id="f466d-139">3.0</span></span> |
| [<span data-ttu-id="f466d-140">ZipArchiveEntry už nezpracovává archivy s nekonzistentními velikostmi záznamů.</span><span class="sxs-lookup"><span data-stu-id="f466d-140">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="f466d-141">3.0</span><span class="sxs-lookup"><span data-stu-id="f466d-141">3.0</span></span> |
| [<span data-ttu-id="f466d-142">Parametr FieldInfo. SetValue vyvolá výjimku pro statická pole pouze pro init.</span><span class="sxs-lookup"><span data-stu-id="f466d-142">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="f466d-143">3.0</span><span class="sxs-lookup"><span data-stu-id="f466d-143">3.0</span></span> |
| [<span data-ttu-id="f466d-144">Soukromá pole přidaná k předdefinovaným typům struktury</span><span class="sxs-lookup"><span data-stu-id="f466d-144">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="f466d-145">2.1</span><span class="sxs-lookup"><span data-stu-id="f466d-145">2.1</span></span> |
| [<span data-ttu-id="f466d-146">Změna výchozí hodnoty UseShellExecute objektu Process</span><span class="sxs-lookup"><span data-stu-id="f466d-146">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="f466d-147">2.1</span><span class="sxs-lookup"><span data-stu-id="f466d-147">2.1</span></span> |
| [<span data-ttu-id="f466d-148">Verze OpenSSL v macOS</span><span class="sxs-lookup"><span data-stu-id="f466d-148">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="f466d-149">2.1</span><span class="sxs-lookup"><span data-stu-id="f466d-149">2.1</span></span> |
| [<span data-ttu-id="f466d-150">UnauthorizedAccessException vyvolaná atributy SystemInfo.</span><span class="sxs-lookup"><span data-stu-id="f466d-150">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="f466d-151">1.0</span><span class="sxs-lookup"><span data-stu-id="f466d-151">1.0</span></span> |
| [<span data-ttu-id="f466d-152">Manipulace s poškozenými výjimkami stavu procesu není podporována.</span><span class="sxs-lookup"><span data-stu-id="f466d-152">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="f466d-153">1.0</span><span class="sxs-lookup"><span data-stu-id="f466d-153">1.0</span></span> |
| [<span data-ttu-id="f466d-154">Vlastnosti objekt UriBuilder protokolu už neobsahují úvodní znaky.</span><span class="sxs-lookup"><span data-stu-id="f466d-154">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="f466d-155">1.0</span><span class="sxs-lookup"><span data-stu-id="f466d-155">1.0</span></span> |
| [<span data-ttu-id="f466d-156">Process. StartInfo vyvolá InvalidOperationException pro procesy, které jste nespustili.</span><span class="sxs-lookup"><span data-stu-id="f466d-156">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="f466d-157">1.0</span><span class="sxs-lookup"><span data-stu-id="f466d-157">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="f466d-158">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f466d-158">.NET 5.0</span></span>

[!INCLUDE [principalpermissionattribute-obsolete](../../../includes/core-changes/corefx/5.0/principalpermissionattribute-obsolete.md)]

***

[!INCLUDE [binaryformatter-serialization-obsolete](../../../includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

***

[!INCLUDE [utf-7-code-paths-obsolete](../../../includes/core-changes/corefx/5.0/utf-7-code-paths-obsolete.md)]

***

[!INCLUDE [vectort-throws-notsupportedexception](../../../includes/core-changes/corefx/5.0/vectort-throws-notsupportedexception.md)]

***

[!INCLUDE [default-activityidformat-changed](../../../includes/core-changes/corefx/5.0/default-activityidformat-changed.md)]

***

[!INCLUDE [vector-lerp-behavior-change](../../../includes/core-changes/corefx/5.0/vector-lerp-behavior-change.md)]

***

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

***

[!INCLUDE [platformabstractions-package-removed](../../../includes/core-changes/corefx/5.0/platformabstractions-package-removed.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="f466d-159">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f466d-159">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="f466d-160">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f466d-160">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="f466d-161">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="f466d-161">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
