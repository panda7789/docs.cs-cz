---
title: Nepodporovaná rozhraní API na jádru rozhraní .NET
titleSuffix: ''
description: Zjistěte, která rozhraní API z rozhraní .NET Framework, která vždy vyvolána výjimku na .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: bd3516d9480ef42b6ea89825ba64867a3ca104e3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242943"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="b7a18-103">Rozhraní API, která vždy vyzvou výjimky na jádru .NET</span><span class="sxs-lookup"><span data-stu-id="b7a18-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="b7a18-104">Následující rozhraní API bude <xref:System.PlatformNotSupportedException> vždy hodit na .NET Core na všech nebo podmnožinu platforem.</span><span class="sxs-lookup"><span data-stu-id="b7a18-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="b7a18-105">Tento článek uspořádá ohrožené členy rozhraní API podle oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b7a18-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="b7a18-106">Tento článek je nedokončená.</span><span class="sxs-lookup"><span data-stu-id="b7a18-106">This article is a work-in-progress.</span></span> <span data-ttu-id="b7a18-107">Není úplný seznam rozhraní API, které vyvolat výjimky na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b7a18-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="b7a18-108">Tento článek neobsahuje explicitní implementace rozhraní pro binární serializaci, které vyvolány na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b7a18-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="b7a18-109">Další informace naleznete [v tématu Binary serializace in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="b7a18-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="b7a18-110">Systém</span><span class="sxs-lookup"><span data-stu-id="b7a18-110">System</span></span>

| <span data-ttu-id="b7a18-111">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-111">Member</span></span> | <span data-ttu-id="b7a18-112">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="b7a18-113">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-114">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="b7a18-115">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="b7a18-116">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-117">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="b7a18-118">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="b7a18-119">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="b7a18-120">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-121">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-122">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="b7a18-123">System.codedom.compiler</span><span class="sxs-lookup"><span data-stu-id="b7a18-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="b7a18-124">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-124">Member</span></span> | <span data-ttu-id="b7a18-125">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="b7a18-126">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="b7a18-127">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="b7a18-128">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="b7a18-129">System.collections.specialized</span><span class="sxs-lookup"><span data-stu-id="b7a18-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="b7a18-130">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-130">Member</span></span> | <span data-ttu-id="b7a18-131">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="b7a18-132">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-133">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-134">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="b7a18-135">System.configuration</span><span class="sxs-lookup"><span data-stu-id="b7a18-135">System.Configuration</span></span>

| <span data-ttu-id="b7a18-136">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-136">Member</span></span> | <span data-ttu-id="b7a18-137">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="b7a18-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType>(všichni členové)</span><span class="sxs-lookup"><span data-stu-id="b7a18-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="b7a18-139">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="b7a18-140">Systém.Konzole</span><span class="sxs-lookup"><span data-stu-id="b7a18-140">System.Console</span></span>

| <span data-ttu-id="b7a18-141">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-141">Member</span></span> | <span data-ttu-id="b7a18-142">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="b7a18-143">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-143">Linux and macOS</span></span> |
| <span data-ttu-id="b7a18-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="b7a18-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b7a18-145">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-145">Linux and macOS</span></span> |
| <span data-ttu-id="b7a18-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="b7a18-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b7a18-147">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-147">Linux and macOS</span></span> |
| <span data-ttu-id="b7a18-148"><xref:System.Console.CursorSize?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="b7a18-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b7a18-149">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-149">Linux and macOS</span></span> |
| <span data-ttu-id="b7a18-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType>(získat pouze)</span><span class="sxs-lookup"><span data-stu-id="b7a18-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="b7a18-151">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="b7a18-152">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="b7a18-153">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="b7a18-154">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-154">Linux and macOS</span></span> |
| <span data-ttu-id="b7a18-155"><xref:System.Console.Title?displayProperty=nameWithType>(získat pouze)</span><span class="sxs-lookup"><span data-stu-id="b7a18-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="b7a18-156">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-156">Linux and macOS</span></span> |
| <span data-ttu-id="b7a18-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="b7a18-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b7a18-158">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-158">Linux and macOS</span></span> |
| <span data-ttu-id="b7a18-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="b7a18-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b7a18-160">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-160">Linux and macOS</span></span> |
| <span data-ttu-id="b7a18-161"><xref:System.Console.WindowTop?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="b7a18-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b7a18-162">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-162">Linux and macOS</span></span> |
| <span data-ttu-id="b7a18-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="b7a18-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b7a18-164">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="b7a18-165">System.data.common</span><span class="sxs-lookup"><span data-stu-id="b7a18-165">System.Data.Common</span></span>

| <span data-ttu-id="b7a18-166">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-166">Member</span></span> | <span data-ttu-id="b7a18-167">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="b7a18-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType><xref:System.NotSupportedException>(hody)</span><span class="sxs-lookup"><span data-stu-id="b7a18-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="b7a18-169">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="b7a18-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="b7a18-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="b7a18-171">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-171">Member</span></span> | <span data-ttu-id="b7a18-172">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="b7a18-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="b7a18-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b7a18-174">Linux</span><span class="sxs-lookup"><span data-stu-id="b7a18-174">Linux</span></span> |
| <span data-ttu-id="b7a18-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="b7a18-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b7a18-176">Linux</span><span class="sxs-lookup"><span data-stu-id="b7a18-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="b7a18-177">macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="b7a18-178">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="b7a18-179">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="b7a18-180">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="b7a18-181">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="b7a18-182">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="b7a18-183">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-183">Linux and macOS</span></span> |
| <span data-ttu-id="b7a18-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="b7a18-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b7a18-185">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-185">Linux and macOS</span></span> |
| <span data-ttu-id="b7a18-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(získat pouze)</span><span class="sxs-lookup"><span data-stu-id="b7a18-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="b7a18-187">macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-187">macOS</span></span> |
| <span data-ttu-id="b7a18-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="b7a18-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b7a18-189">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="b7a18-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="b7a18-190">System.IO</span></span>

| <span data-ttu-id="b7a18-191">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-191">Member</span></span> | <span data-ttu-id="b7a18-192">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="b7a18-193">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-194">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="b7a18-195">System.io.pipes</span><span class="sxs-lookup"><span data-stu-id="b7a18-195">System.IO.Pipes</span></span>

| <span data-ttu-id="b7a18-196">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-196">Member</span></span> | <span data-ttu-id="b7a18-197">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="b7a18-198">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="b7a18-199">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="b7a18-200">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="b7a18-201">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-201">Linux and macOS</span></span> |
| <span data-ttu-id="b7a18-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="b7a18-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b7a18-203">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="b7a18-204">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="b7a18-205">System.media</span><span class="sxs-lookup"><span data-stu-id="b7a18-205">System.Media</span></span>

| <span data-ttu-id="b7a18-206">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-206">Member</span></span> | <span data-ttu-id="b7a18-207">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="b7a18-208">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="b7a18-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="b7a18-209">System.Net</span></span>

| <span data-ttu-id="b7a18-210">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-210">Member</span></span> | <span data-ttu-id="b7a18-211">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-212">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-213">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="b7a18-214">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-215">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="b7a18-216">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-217">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="b7a18-218">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-219">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="b7a18-220">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-221">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="b7a18-222">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="b7a18-223">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="b7a18-224">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="b7a18-225">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-226">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="b7a18-227">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-228">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="b7a18-229">System.net.networkinformation</span><span class="sxs-lookup"><span data-stu-id="b7a18-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="b7a18-230">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-230">Member</span></span> | <span data-ttu-id="b7a18-231">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="b7a18-232">Windows (UPW)</span><span class="sxs-lookup"><span data-stu-id="b7a18-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="b7a18-233">System.net.sockets</span><span class="sxs-lookup"><span data-stu-id="b7a18-233">System.Net.Sockets</span></span>

| <span data-ttu-id="b7a18-234">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-234">Member</span></span> | <span data-ttu-id="b7a18-235">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="b7a18-236">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-237">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="b7a18-238">Server System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="b7a18-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="b7a18-239">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-239">Member</span></span> | <span data-ttu-id="b7a18-240">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="b7a18-241">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="b7a18-242">System.reflection</span><span class="sxs-lookup"><span data-stu-id="b7a18-242">System.Reflection</span></span>

| <span data-ttu-id="b7a18-243">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-243">Member</span></span> | <span data-ttu-id="b7a18-244">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="b7a18-245">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-246">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-247">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-248">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="b7a18-249">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="b7a18-250">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="b7a18-251">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="b7a18-252">System.runtime.compilerservices</span><span class="sxs-lookup"><span data-stu-id="b7a18-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="b7a18-253">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-253">Member</span></span> | <span data-ttu-id="b7a18-254">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="b7a18-255">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="b7a18-256">System.runtime.interopservices</span><span class="sxs-lookup"><span data-stu-id="b7a18-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="b7a18-257">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-257">Member</span></span> | <span data-ttu-id="b7a18-258">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-259">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="b7a18-260">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-261">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-262">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-263">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-264">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-265">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="b7a18-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="b7a18-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="b7a18-267">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-267">Member</span></span> | <span data-ttu-id="b7a18-268">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="b7a18-269">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="b7a18-270">System.security</span><span class="sxs-lookup"><span data-stu-id="b7a18-270">System.Security</span></span>

| <span data-ttu-id="b7a18-271">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-271">Member</span></span> | <span data-ttu-id="b7a18-272">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="b7a18-273">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="b7a18-274">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-275">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="b7a18-276">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="b7a18-277">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="b7a18-278">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="b7a18-279">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="b7a18-280">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="b7a18-281">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="b7a18-282">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="b7a18-283">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-284">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="b7a18-285">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="b7a18-286">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="b7a18-287">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="b7a18-287">System.Security.Claims</span></span>

| <span data-ttu-id="b7a18-288">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-288">Member</span></span> | <span data-ttu-id="b7a18-289">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor> | <span data-ttu-id="b7a18-290">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-291">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="b7a18-292">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="b7a18-293">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-294">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="b7a18-295">System.security.cryptography</span><span class="sxs-lookup"><span data-stu-id="b7a18-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="b7a18-296">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-296">Member</span></span> | <span data-ttu-id="b7a18-297">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-298">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="b7a18-299">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="b7a18-300">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="b7a18-301">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="b7a18-302">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="b7a18-303">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="b7a18-304">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="b7a18-305">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="b7a18-306">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="b7a18-307">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="b7a18-308">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="b7a18-309">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="b7a18-310">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="b7a18-311">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="b7a18-312">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="b7a18-313">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-314">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="b7a18-315">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="b7a18-316">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="b7a18-317">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="b7a18-318">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-319">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="b7a18-320">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="b7a18-321">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b7a18-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="b7a18-322">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="b7a18-323">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="b7a18-324">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-325">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="b7a18-326">System.security.cryptography.pkcs</span><span class="sxs-lookup"><span data-stu-id="b7a18-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="b7a18-327">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-327">Member</span></span> | <span data-ttu-id="b7a18-328">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="b7a18-329">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-330">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="b7a18-331">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="b7a18-332">System.Security.Cryptography.X509Certifikáty</span><span class="sxs-lookup"><span data-stu-id="b7a18-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="b7a18-333">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-333">Member</span></span> | <span data-ttu-id="b7a18-334">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="b7a18-335">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="b7a18-336">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="b7a18-337">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-337">All</span></span> |
| <span data-ttu-id="b7a18-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType>(pouze sada)</span><span class="sxs-lookup"><span data-stu-id="b7a18-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b7a18-339">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="b7a18-340">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="b7a18-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="b7a18-341">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-341">Member</span></span> | <span data-ttu-id="b7a18-342">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="b7a18-343">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="b7a18-344">System.security.policy</span><span class="sxs-lookup"><span data-stu-id="b7a18-344">System.Security.Policy</span></span>

| <span data-ttu-id="b7a18-345">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-345">Member</span></span> | <span data-ttu-id="b7a18-346">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-347">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="b7a18-348">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="b7a18-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="b7a18-349">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-349">Member</span></span> | <span data-ttu-id="b7a18-350">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="b7a18-351">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="b7a18-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="b7a18-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="b7a18-353">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-353">Member</span></span> | <span data-ttu-id="b7a18-354">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="b7a18-355">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="b7a18-356">System.threading</span><span class="sxs-lookup"><span data-stu-id="b7a18-356">System.Threading</span></span>

| <span data-ttu-id="b7a18-357">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-357">Member</span></span> | <span data-ttu-id="b7a18-358">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-359">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-360">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="b7a18-361">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="b7a18-362">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="b7a18-363">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="b7a18-364">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="b7a18-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="b7a18-365">System.Xml</span></span>

| <span data-ttu-id="b7a18-366">Člen</span><span class="sxs-lookup"><span data-stu-id="b7a18-366">Member</span></span> | <span data-ttu-id="b7a18-367">Platformy, které hází</span><span class="sxs-lookup"><span data-stu-id="b7a18-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-368">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-369">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="b7a18-370">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7a18-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="b7a18-371">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7a18-371">See also</span></span>

- [<span data-ttu-id="b7a18-372">Nejnovější změny pro migraci z rozhraní .NET Framework na .NET Core</span><span class="sxs-lookup"><span data-stu-id="b7a18-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="b7a18-373">Binární serializace v jádru .NET Core</span><span class="sxs-lookup"><span data-stu-id="b7a18-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="b7a18-374">Analyzátor přenositelnosti .NET</span><span class="sxs-lookup"><span data-stu-id="b7a18-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
