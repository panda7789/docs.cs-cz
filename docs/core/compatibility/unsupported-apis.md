---
title: Nepodporovaná rozhraní API na jádru rozhraní .NET
titleSuffix: ''
description: Zjistěte, která rozhraní API z rozhraní .NET Framework, která vždy vyvolána výjimku na .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: c4b94321d30cacd90d5c2ee23c258681683a6faa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092964"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="be536-103">Rozhraní API, která vždy vyzvou výjimky na jádru .NET</span><span class="sxs-lookup"><span data-stu-id="be536-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="be536-104">Následující rozhraní API bude <xref:System.PlatformNotSupportedException> vždy hodit na .NET Core na všech nebo podmnožinu platforem.</span><span class="sxs-lookup"><span data-stu-id="be536-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="be536-105">Tento článek uspořádá ohrožené členy rozhraní API podle oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="be536-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="be536-106">Tento článek je nedokončená.</span><span class="sxs-lookup"><span data-stu-id="be536-106">This article is a work-in-progress.</span></span> <span data-ttu-id="be536-107">Není úplný seznam rozhraní API, které vyvolat výjimky na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="be536-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="be536-108">Tento článek neobsahuje explicitní implementace rozhraní pro binární serializaci, které vyvolány na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="be536-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="be536-109">Další informace naleznete [v tématu Binary serializace in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="be536-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="be536-110">Systémový</span><span class="sxs-lookup"><span data-stu-id="be536-110">System</span></span>

| <span data-ttu-id="be536-111">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-111">Member</span></span> | <span data-ttu-id="be536-112">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-113">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="be536-114">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="be536-115">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="be536-116">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-117">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="be536-118">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="be536-119">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="be536-120">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-121">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="be536-122">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="be536-123">System.codedom.compiler</span><span class="sxs-lookup"><span data-stu-id="be536-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="be536-124">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-124">Member</span></span> | <span data-ttu-id="be536-125">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-126">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-127">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-128">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="be536-129">System.collections.specialized</span><span class="sxs-lookup"><span data-stu-id="be536-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="be536-130">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-130">Member</span></span> | <span data-ttu-id="be536-131">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-132">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-133">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="be536-134">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="be536-135">System.configuration</span><span class="sxs-lookup"><span data-stu-id="be536-135">System.Configuration</span></span>

| <span data-ttu-id="be536-136">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-136">Member</span></span> | <span data-ttu-id="be536-137">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="be536-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType>(všichni členové)</span><span class="sxs-lookup"><span data-stu-id="be536-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="be536-139">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="be536-140">Systém.Konzole</span><span class="sxs-lookup"><span data-stu-id="be536-140">System.Console</span></span>

| <span data-ttu-id="be536-141">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-141">Member</span></span> | <span data-ttu-id="be536-142">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="be536-143">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-143">Linux and macOS</span></span> |
| <span data-ttu-id="be536-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="be536-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="be536-145">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-145">Linux and macOS</span></span> |
| <span data-ttu-id="be536-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="be536-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="be536-147">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-147">Linux and macOS</span></span> |
| <span data-ttu-id="be536-148"><xref:System.Console.CursorSize?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="be536-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="be536-149">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-149">Linux and macOS</span></span> |
| <span data-ttu-id="be536-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType>(získat pouze)</span><span class="sxs-lookup"><span data-stu-id="be536-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="be536-151">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-152">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-153">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-154">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-154">Linux and macOS</span></span> |
| <span data-ttu-id="be536-155"><xref:System.Console.Title?displayProperty=nameWithType>(získat pouze)</span><span class="sxs-lookup"><span data-stu-id="be536-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="be536-156">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-156">Linux and macOS</span></span> |
| <span data-ttu-id="be536-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="be536-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="be536-158">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-158">Linux and macOS</span></span> |
| <span data-ttu-id="be536-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="be536-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="be536-160">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-160">Linux and macOS</span></span> |
| <span data-ttu-id="be536-161"><xref:System.Console.WindowTop?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="be536-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="be536-162">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-162">Linux and macOS</span></span> |
| <span data-ttu-id="be536-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="be536-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="be536-164">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="be536-165">System.data.common</span><span class="sxs-lookup"><span data-stu-id="be536-165">System.Data.Common</span></span>

| <span data-ttu-id="be536-166">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-166">Member</span></span> | <span data-ttu-id="be536-167">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="be536-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType><xref:System.NotSupportedException>(hody)</span><span class="sxs-lookup"><span data-stu-id="be536-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="be536-169">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="be536-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="be536-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="be536-171">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-171">Member</span></span> | <span data-ttu-id="be536-172">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="be536-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="be536-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="be536-174">Linux</span><span class="sxs-lookup"><span data-stu-id="be536-174">Linux</span></span> |
| <span data-ttu-id="be536-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="be536-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="be536-176">Linux</span><span class="sxs-lookup"><span data-stu-id="be536-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="be536-177">macOS</span><span class="sxs-lookup"><span data-stu-id="be536-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="be536-178">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-179">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="be536-180">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="be536-181">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="be536-182">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="be536-183">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-183">Linux and macOS</span></span> |
| <span data-ttu-id="be536-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="be536-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="be536-185">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-185">Linux and macOS</span></span> |
| <span data-ttu-id="be536-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(získat pouze)</span><span class="sxs-lookup"><span data-stu-id="be536-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="be536-187">macOS</span><span class="sxs-lookup"><span data-stu-id="be536-187">macOS</span></span> |
| <span data-ttu-id="be536-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="be536-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="be536-189">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="be536-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="be536-190">System.IO</span></span>

| <span data-ttu-id="be536-191">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-191">Member</span></span> | <span data-ttu-id="be536-192">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-193">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-194">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="be536-195">System.io.pipes</span><span class="sxs-lookup"><span data-stu-id="be536-195">System.IO.Pipes</span></span>

| <span data-ttu-id="be536-196">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-196">Member</span></span> | <span data-ttu-id="be536-197">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="be536-198">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="be536-199">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="be536-200">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="be536-201">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-201">Linux and macOS</span></span> |
| <span data-ttu-id="be536-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="be536-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="be536-203">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="be536-204">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="be536-205">System.media</span><span class="sxs-lookup"><span data-stu-id="be536-205">System.Media</span></span>

| <span data-ttu-id="be536-206">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-206">Member</span></span> | <span data-ttu-id="be536-207">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-208">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="be536-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="be536-209">System.Net</span></span>

| <span data-ttu-id="be536-210">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-210">Member</span></span> | <span data-ttu-id="be536-211">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="be536-212">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="be536-213">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-214">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-215">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-216">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-217">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-218">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-219">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-220">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-221">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-222">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="be536-223">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-224">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-225">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-226">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-227">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-228">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="be536-229">System.net.networkinformation</span><span class="sxs-lookup"><span data-stu-id="be536-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="be536-230">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-230">Member</span></span> | <span data-ttu-id="be536-231">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-232">Windows (UPW)</span><span class="sxs-lookup"><span data-stu-id="be536-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="be536-233">System.net.sockets</span><span class="sxs-lookup"><span data-stu-id="be536-233">System.Net.Sockets</span></span>

| <span data-ttu-id="be536-234">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-234">Member</span></span> | <span data-ttu-id="be536-235">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)?displayProperty=nameWithType> | <span data-ttu-id="be536-236">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="be536-237">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="be536-238">Server System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="be536-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="be536-239">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-239">Member</span></span> | <span data-ttu-id="be536-240">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="be536-241">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="be536-242">System.reflection</span><span class="sxs-lookup"><span data-stu-id="be536-242">System.Reflection</span></span>

| <span data-ttu-id="be536-243">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-243">Member</span></span> | <span data-ttu-id="be536-244">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-245">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="be536-246">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-247">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="be536-248">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | <span data-ttu-id="be536-249">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-250">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="be536-251">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="be536-252">System.runtime.compilerservices</span><span class="sxs-lookup"><span data-stu-id="be536-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="be536-253">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-253">Member</span></span> | <span data-ttu-id="be536-254">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="be536-255">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="be536-256">System.runtime.interopservices</span><span class="sxs-lookup"><span data-stu-id="be536-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="be536-257">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-257">Member</span></span> | <span data-ttu-id="be536-258">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="be536-259">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="be536-260">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="be536-261">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="be536-262">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="be536-263">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="be536-264">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="be536-265">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="be536-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="be536-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="be536-267">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-267">Member</span></span> | <span data-ttu-id="be536-268">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="be536-269">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="be536-270">System.security</span><span class="sxs-lookup"><span data-stu-id="be536-270">System.Security</span></span>

| <span data-ttu-id="be536-271">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-271">Member</span></span> | <span data-ttu-id="be536-272">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="be536-273">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="be536-274">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="be536-275">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="be536-276">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="be536-277">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="be536-278">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="be536-279">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="be536-280">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="be536-281">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="be536-282">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="be536-283">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="be536-284">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="be536-285">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="be536-286">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="be536-287">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="be536-287">System.Security.Claims</span></span>

| <span data-ttu-id="be536-288">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-288">Member</span></span> | <span data-ttu-id="be536-289">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | <span data-ttu-id="be536-290">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-291">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | <span data-ttu-id="be536-292">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-293">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-294">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="be536-295">System.security.cryptography</span><span class="sxs-lookup"><span data-stu-id="be536-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="be536-296">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-296">Member</span></span> | <span data-ttu-id="be536-297">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="be536-298">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-299">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="be536-300">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="be536-301">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="be536-302">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="be536-303">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="be536-304">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="be536-305">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="be536-306">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="be536-307">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="be536-308">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="be536-309">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="be536-310">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="be536-311">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="be536-312">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="be536-313">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="be536-314">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-315">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-316">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-317">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="be536-318">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="be536-319">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-320">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-321">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="be536-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-322">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-323">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="be536-324">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="be536-325">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="be536-326">System.security.cryptography.pkcs</span><span class="sxs-lookup"><span data-stu-id="be536-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="be536-327">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-327">Member</span></span> | <span data-ttu-id="be536-328">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | <span data-ttu-id="be536-329">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="be536-330">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="be536-331">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="be536-332">System.Security.Cryptography.X509Certifikáty</span><span class="sxs-lookup"><span data-stu-id="be536-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="be536-333">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-333">Member</span></span> | <span data-ttu-id="be536-334">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-335">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-336">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-337">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-337">All</span></span> |
| <span data-ttu-id="be536-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="be536-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="be536-339">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="be536-340">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="be536-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="be536-341">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-341">Member</span></span> | <span data-ttu-id="be536-342">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-343">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="be536-344">System.security.policy</span><span class="sxs-lookup"><span data-stu-id="be536-344">System.Security.Policy</span></span>

| <span data-ttu-id="be536-345">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-345">Member</span></span> | <span data-ttu-id="be536-346">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-347">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="be536-348">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="be536-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="be536-349">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-349">Member</span></span> | <span data-ttu-id="be536-350">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-351">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="be536-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="be536-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="be536-353">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-353">Member</span></span> | <span data-ttu-id="be536-354">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-355">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="be536-356">System.threading</span><span class="sxs-lookup"><span data-stu-id="be536-356">System.Threading</span></span>

| <span data-ttu-id="be536-357">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-357">Member</span></span> | <span data-ttu-id="be536-358">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-359">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="be536-360">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="be536-361">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="be536-362">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="be536-363">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="be536-364">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="be536-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="be536-365">System.Xml</span></span>

| <span data-ttu-id="be536-366">Člen</span><span class="sxs-lookup"><span data-stu-id="be536-366">Member</span></span> | <span data-ttu-id="be536-367">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="be536-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="be536-368">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="be536-369">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="be536-370">Všechny</span><span class="sxs-lookup"><span data-stu-id="be536-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="be536-371">Viz také</span><span class="sxs-lookup"><span data-stu-id="be536-371">See also</span></span>

- [<span data-ttu-id="be536-372">Nejnovější změny pro migraci z rozhraní .NET Framework na .NET Core</span><span class="sxs-lookup"><span data-stu-id="be536-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="be536-373">Binární serializace v jádru .NET Core</span><span class="sxs-lookup"><span data-stu-id="be536-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="be536-374">Analyzátor přenositelnosti .NET</span><span class="sxs-lookup"><span data-stu-id="be536-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
