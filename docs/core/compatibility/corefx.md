---
title: Přerušující změny knihovny základních tříd
description: Obsahuje seznam nejnovějších změn v základních knihovnách .NET.
ms.date: 07/27/2020
ms.openlocfilehash: 8b8fb9b88edf4f1e5f83ef7c21f1712af40479fd
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359130"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="3831d-103">Základní knihovny .NET – přerušující změny</span><span class="sxs-lookup"><span data-stu-id="3831d-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="3831d-104">Základní knihovny .NET poskytují primitivní a další obecné typy používané .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3831d-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="3831d-105">Na této stránce jsou popsány následující přerušující se změny:</span><span class="sxs-lookup"><span data-stu-id="3831d-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="3831d-106">Zásadní změna</span><span class="sxs-lookup"><span data-stu-id="3831d-106">Breaking change</span></span> | <span data-ttu-id="3831d-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="3831d-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="3831d-108">U vnořených typů se můžou u vnitřních typů lišit.</span><span class="sxs-lookup"><span data-stu-id="3831d-108">Hardware intrinsic IsSupported checks may differ for nested types</span></span>](#hardware-intrinsic-issupported-checks-may-differ-for-nested-types) | <span data-ttu-id="3831d-109">5,0</span><span class="sxs-lookup"><span data-stu-id="3831d-109">5.0</span></span> |
| [<span data-ttu-id="3831d-110">Názvy parametrů se změnily v referenčních sestaveních.</span><span class="sxs-lookup"><span data-stu-id="3831d-110">Parameter names changed in reference assemblies</span></span>](#parameter-names-changed-in-reference-assemblies) | <span data-ttu-id="3831d-111">5,0</span><span class="sxs-lookup"><span data-stu-id="3831d-111">5.0</span></span> |
| [<span data-ttu-id="3831d-112">Cesty URI bez znaků, které nejsou ASCII, se v systému UNIX analyzují správně</span><span class="sxs-lookup"><span data-stu-id="3831d-112">URI paths with non-ASCII characters parse correctly on Unix</span></span>](#uri-paths-with-non-ascii-characters-parse-correctly-on-unix) | <span data-ttu-id="3831d-113">5,0</span><span class="sxs-lookup"><span data-stu-id="3831d-113">5.0</span></span> |
| [<span data-ttu-id="3831d-114">Rozpoznání identifikátoru URI cest UNC v systému UNIX</span><span class="sxs-lookup"><span data-stu-id="3831d-114">Uri recognition of UNC paths on Unix</span></span>](#uri-recognition-of-unc-paths-on-unix) | <span data-ttu-id="3831d-115">5,0</span><span class="sxs-lookup"><span data-stu-id="3831d-115">5.0</span></span> |
| [<span data-ttu-id="3831d-116">Environment. OSVersion vrátí správnou verzi operačního systému.</span><span class="sxs-lookup"><span data-stu-id="3831d-116">Environment.OSVersion returns the correct operating system version</span></span>](#environmentosversion-returns-the-correct-operating-system-version) | <span data-ttu-id="3831d-117">5,0</span><span class="sxs-lookup"><span data-stu-id="3831d-117">5.0</span></span> |
| [<span data-ttu-id="3831d-118">Složitost LINQ OrderBy. First {OrDefault} se zvýšila.</span><span class="sxs-lookup"><span data-stu-id="3831d-118">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>](#complexity-of-linq-orderbyfirstordefault-increased) | <span data-ttu-id="3831d-119">5,0</span><span class="sxs-lookup"><span data-stu-id="3831d-119">5.0</span></span> |
| [<span data-ttu-id="3831d-120">IntPtr a UIntPtr implementují IFormattable</span><span class="sxs-lookup"><span data-stu-id="3831d-120">IntPtr and UIntPtr implement IFormattable</span></span>](#intptr-and-uintptr-implement-iformattable) | <span data-ttu-id="3831d-121">5,0</span><span class="sxs-lookup"><span data-stu-id="3831d-121">5.0</span></span> |
| [<span data-ttu-id="3831d-122">PrincipalPermissionAttribute je zastaralá jako chyba.</span><span class="sxs-lookup"><span data-stu-id="3831d-122">PrincipalPermissionAttribute is obsolete as error</span></span>](#principalpermissionattribute-is-obsolete-as-error) | <span data-ttu-id="3831d-123">5,0</span><span class="sxs-lookup"><span data-stu-id="3831d-123">5.0</span></span> |
| [<span data-ttu-id="3831d-124">Metody serializace BinaryFormatter jsou zastaralé a zakázané v aplikacích ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3831d-124">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | <span data-ttu-id="3831d-125">5,0</span><span class="sxs-lookup"><span data-stu-id="3831d-125">5.0</span></span> |
| [<span data-ttu-id="3831d-126">Cesty kódu UTF-7 jsou zastaralé.</span><span class="sxs-lookup"><span data-stu-id="3831d-126">UTF-7 code paths are obsolete</span></span>](#utf-7-code-paths-are-obsolete) | <span data-ttu-id="3831d-127">5,0</span><span class="sxs-lookup"><span data-stu-id="3831d-127">5.0</span></span> |
| [<span data-ttu-id="3831d-128">Vector \<T> vždy vyvolá NotSupportedException pro nepodporované typy</span><span class="sxs-lookup"><span data-stu-id="3831d-128">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="3831d-129">5,0</span><span class="sxs-lookup"><span data-stu-id="3831d-129">5.0</span></span> |
| [<span data-ttu-id="3831d-130">Výchozí ActivityIdFormat je W3C.</span><span class="sxs-lookup"><span data-stu-id="3831d-130">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="3831d-131">5,0</span><span class="sxs-lookup"><span data-stu-id="3831d-131">5.0</span></span> |
| [<span data-ttu-id="3831d-132">Změna chování pro Vector2. lerp a Vector4. lerp</span><span class="sxs-lookup"><span data-stu-id="3831d-132">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="3831d-133">5,0</span><span class="sxs-lookup"><span data-stu-id="3831d-133">5.0</span></span> |
| [<span data-ttu-id="3831d-134">Metody SSE a SSE2 CompareGreaterThan správně zpracovávají vstupy NaN.</span><span class="sxs-lookup"><span data-stu-id="3831d-134">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="3831d-135">5,0</span><span class="sxs-lookup"><span data-stu-id="3831d-135">5.0</span></span> |
| [<span data-ttu-id="3831d-136">Sada CounterSet. provedení operace CreateCounterSetInstance nyní vyvolá chybu InvalidOperationException, pokud již instance existuje.</span><span class="sxs-lookup"><span data-stu-id="3831d-136">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="3831d-137">5,0</span><span class="sxs-lookup"><span data-stu-id="3831d-137">5.0</span></span> |
| [<span data-ttu-id="3831d-138">Balíček Microsoft. DotNet. PlatformAbstractions se odebral.</span><span class="sxs-lookup"><span data-stu-id="3831d-138">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="3831d-139">5,0</span><span class="sxs-lookup"><span data-stu-id="3831d-139">5.0</span></span> |
| [<span data-ttu-id="3831d-140">Rozhraní API, která verze sestav nyní hlásí produkt a nikoli verzi souboru</span><span class="sxs-lookup"><span data-stu-id="3831d-140">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="3831d-141">3,0</span><span class="sxs-lookup"><span data-stu-id="3831d-141">3.0</span></span> |
| [<span data-ttu-id="3831d-142">Vlastní instance EncoderFallbackBuffer se nemůžou vrátit rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="3831d-142">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="3831d-143">3,0</span><span class="sxs-lookup"><span data-stu-id="3831d-143">3.0</span></span> |
| [<span data-ttu-id="3831d-144">Změny chování při formátování a analýze plovoucí desetinné čárky</span><span class="sxs-lookup"><span data-stu-id="3831d-144">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="3831d-145">3,0</span><span class="sxs-lookup"><span data-stu-id="3831d-145">3.0</span></span> |
| [<span data-ttu-id="3831d-146">Operace analýzy s plovoucí desetinnou čárkou již nejsou úspěšné nebo vyvolávají výjimku OverflowException</span><span class="sxs-lookup"><span data-stu-id="3831d-146">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="3831d-147">3,0</span><span class="sxs-lookup"><span data-stu-id="3831d-147">3.0</span></span> |
| [<span data-ttu-id="3831d-148">InvalidAsynchronousStateException – přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="3831d-148">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="3831d-149">3,0</span><span class="sxs-lookup"><span data-stu-id="3831d-149">3.0</span></span> |
| [<span data-ttu-id="3831d-150">Výměna chybně formátovaných sekvencí UTF-8 se řídí pokyny pro kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="3831d-150">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="3831d-151">3,0</span><span class="sxs-lookup"><span data-stu-id="3831d-151">3.0</span></span> |
| [<span data-ttu-id="3831d-152">TypeDescriptionProviderAttribute přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="3831d-152">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="3831d-153">3,0</span><span class="sxs-lookup"><span data-stu-id="3831d-153">3.0</span></span> |
| [<span data-ttu-id="3831d-154">ZipArchiveEntry už nezpracovává archivy s nekonzistentními velikostmi záznamů.</span><span class="sxs-lookup"><span data-stu-id="3831d-154">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="3831d-155">3,0</span><span class="sxs-lookup"><span data-stu-id="3831d-155">3.0</span></span> |
| [<span data-ttu-id="3831d-156">Parametr FieldInfo. SetValue vyvolá výjimku pro statická pole pouze pro init.</span><span class="sxs-lookup"><span data-stu-id="3831d-156">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="3831d-157">3,0</span><span class="sxs-lookup"><span data-stu-id="3831d-157">3.0</span></span> |
| [<span data-ttu-id="3831d-158">Soukromá pole přidaná k předdefinovaným typům struktury</span><span class="sxs-lookup"><span data-stu-id="3831d-158">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="3831d-159">2.1</span><span class="sxs-lookup"><span data-stu-id="3831d-159">2.1</span></span> |
| [<span data-ttu-id="3831d-160">Změna výchozí hodnoty UseShellExecute objektu Process</span><span class="sxs-lookup"><span data-stu-id="3831d-160">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="3831d-161">2.1</span><span class="sxs-lookup"><span data-stu-id="3831d-161">2.1</span></span> |
| [<span data-ttu-id="3831d-162">Verze OpenSSL v macOS</span><span class="sxs-lookup"><span data-stu-id="3831d-162">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="3831d-163">2.1</span><span class="sxs-lookup"><span data-stu-id="3831d-163">2.1</span></span> |
| [<span data-ttu-id="3831d-164">UnauthorizedAccessException vyvolaná atributy SystemInfo.</span><span class="sxs-lookup"><span data-stu-id="3831d-164">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="3831d-165">1,0</span><span class="sxs-lookup"><span data-stu-id="3831d-165">1.0</span></span> |
| [<span data-ttu-id="3831d-166">Manipulace s poškozenými výjimkami stavu procesu není podporována.</span><span class="sxs-lookup"><span data-stu-id="3831d-166">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="3831d-167">1,0</span><span class="sxs-lookup"><span data-stu-id="3831d-167">1.0</span></span> |
| [<span data-ttu-id="3831d-168">Vlastnosti objekt UriBuilder protokolu už neobsahují úvodní znaky.</span><span class="sxs-lookup"><span data-stu-id="3831d-168">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="3831d-169">1,0</span><span class="sxs-lookup"><span data-stu-id="3831d-169">1.0</span></span> |
| [<span data-ttu-id="3831d-170">Process. StartInfo vyvolá InvalidOperationException pro procesy, které jste nespustili.</span><span class="sxs-lookup"><span data-stu-id="3831d-170">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="3831d-171">1,0</span><span class="sxs-lookup"><span data-stu-id="3831d-171">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="3831d-172">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="3831d-172">.NET 5.0</span></span>

[!INCLUDE [hardware-instrinsics-issupported-checks](../../../includes/core-changes/corefx/5.0/hardware-instrinsics-issupported-checks.md)]

***

[!INCLUDE [reference-assembly-parameter-names](../../../includes/core-changes/corefx/5.0/reference-assembly-parameter-names.md)]

***

[!INCLUDE [non-ascii-chars-in-uri-parsed-correctly](../../../includes/core-changes/corefx/5.0/non-ascii-chars-in-uri-parsed-correctly.md)]

***

[!INCLUDE [unc-path-recognition-unix](../../../includes/core-changes/corefx/5.0/unc-path-recognition-unix.md)]

***

[!INCLUDE [environment-osversion-returns-correct-version](../../../includes/core-changes/corefx/5.0/environment-osversion-returns-correct-version.md)]

***

[!INCLUDE [orderby-firstordefault-complexity-increase](../../../includes/core-changes/corefx/5.0/orderby-firstordefault-complexity-increase.md)]

***

[!INCLUDE [intptr-uintptr-implement-iformattable](../../../includes/core-changes/corefx/5.0/intptr-uintptr-implement-iformattable.md)]

***

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

## <a name="net-core-30"></a><span data-ttu-id="3831d-173">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3831d-173">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="3831d-174">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3831d-174">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="3831d-175">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="3831d-175">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
