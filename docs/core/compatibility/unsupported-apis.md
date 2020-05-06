---
title: Nepodporovaná rozhraní API v .NET Core
titleSuffix: ''
description: Seznamte se s rozhraními API z .NET Framework, která vždy vyvolají výjimku pro .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: 941e9149c7679afe4a888149108d0a9a28e5e7ab
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794595"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="e0845-103">Rozhraní API, která vždy vyvolávají výjimky v .NET Core</span><span class="sxs-lookup"><span data-stu-id="e0845-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="e0845-104">Následující rozhraní API se vždy vyvolají <xref:System.PlatformNotSupportedException> na .NET Core ve všech nebo v podmnožině platforem.</span><span class="sxs-lookup"><span data-stu-id="e0845-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="e0845-105">Tento článek uspořádá ovlivněné členy rozhraní API podle oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e0845-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="e0845-106">Tento článek je nedokončený.</span><span class="sxs-lookup"><span data-stu-id="e0845-106">This article is a work-in-progress.</span></span> <span data-ttu-id="e0845-107">Nejedná se o úplný seznam rozhraní API, která vyvolávají výjimky v rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0845-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="e0845-108">Tento článek nezahrnuje implementace explicitního rozhraní pro binární serializaci, která se vyvolává v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0845-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="e0845-109">Další informace najdete v tématu [binární serializace v .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="e0845-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="e0845-110">Systém</span><span class="sxs-lookup"><span data-stu-id="e0845-110">System</span></span>

| <span data-ttu-id="e0845-111">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-111">Member</span></span> | <span data-ttu-id="e0845-112">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="e0845-113">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="e0845-114">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="e0845-115">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="e0845-116">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e0845-117">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="e0845-118">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="e0845-119">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="e0845-120">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e0845-121">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="e0845-122">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="e0845-123">System. CodeDom. Compiler</span><span class="sxs-lookup"><span data-stu-id="e0845-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="e0845-124">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-124">Member</span></span> | <span data-ttu-id="e0845-125">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="e0845-126">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="e0845-127">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="e0845-128">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="e0845-129">System. Collections. specialize</span><span class="sxs-lookup"><span data-stu-id="e0845-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="e0845-130">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-130">Member</span></span> | <span data-ttu-id="e0845-131">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e0845-132">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e0845-133">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="e0845-134">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="e0845-135">System. Configuration</span><span class="sxs-lookup"><span data-stu-id="e0845-135">System.Configuration</span></span>

| <span data-ttu-id="e0845-136">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-136">Member</span></span> | <span data-ttu-id="e0845-137">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="e0845-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType>(všichni členové)</span><span class="sxs-lookup"><span data-stu-id="e0845-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="e0845-139">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="e0845-140">System. Console</span><span class="sxs-lookup"><span data-stu-id="e0845-140">System.Console</span></span>

| <span data-ttu-id="e0845-141">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-141">Member</span></span> | <span data-ttu-id="e0845-142">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="e0845-143">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-143">Linux and macOS</span></span> |
| <span data-ttu-id="e0845-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType>(jenom nastavit)</span><span class="sxs-lookup"><span data-stu-id="e0845-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e0845-145">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-145">Linux and macOS</span></span> |
| <span data-ttu-id="e0845-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType>(jenom nastavit)</span><span class="sxs-lookup"><span data-stu-id="e0845-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e0845-147">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-147">Linux and macOS</span></span> |
| <span data-ttu-id="e0845-148"><xref:System.Console.CursorSize?displayProperty=nameWithType>(jenom nastavit)</span><span class="sxs-lookup"><span data-stu-id="e0845-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e0845-149">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-149">Linux and macOS</span></span> |
| <span data-ttu-id="e0845-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType>(jenom pro Get)</span><span class="sxs-lookup"><span data-stu-id="e0845-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="e0845-151">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="e0845-152">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="e0845-153">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="e0845-154">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-154">Linux and macOS</span></span> |
| <span data-ttu-id="e0845-155"><xref:System.Console.Title?displayProperty=nameWithType>(jenom pro Get)</span><span class="sxs-lookup"><span data-stu-id="e0845-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="e0845-156">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-156">Linux and macOS</span></span> |
| <span data-ttu-id="e0845-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType>(jenom nastavit)</span><span class="sxs-lookup"><span data-stu-id="e0845-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e0845-158">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-158">Linux and macOS</span></span> |
| <span data-ttu-id="e0845-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType>(jenom nastavit)</span><span class="sxs-lookup"><span data-stu-id="e0845-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e0845-160">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-160">Linux and macOS</span></span> |
| <span data-ttu-id="e0845-161"><xref:System.Console.WindowTop?displayProperty=nameWithType>(jenom nastavit)</span><span class="sxs-lookup"><span data-stu-id="e0845-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e0845-162">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-162">Linux and macOS</span></span> |
| <span data-ttu-id="e0845-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType>(jenom nastavit)</span><span class="sxs-lookup"><span data-stu-id="e0845-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e0845-164">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="e0845-165">System. data. Common</span><span class="sxs-lookup"><span data-stu-id="e0845-165">System.Data.Common</span></span>

| <span data-ttu-id="e0845-166">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-166">Member</span></span> | <span data-ttu-id="e0845-167">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="e0845-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType>(vyvolá <xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="e0845-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="e0845-169">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="e0845-170">System. Diagnostics. Process</span><span class="sxs-lookup"><span data-stu-id="e0845-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="e0845-171">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-171">Member</span></span> | <span data-ttu-id="e0845-172">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="e0845-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType>(jenom nastavit)</span><span class="sxs-lookup"><span data-stu-id="e0845-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e0845-174">Linux</span><span class="sxs-lookup"><span data-stu-id="e0845-174">Linux</span></span> |
| <span data-ttu-id="e0845-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType>(jenom nastavit)</span><span class="sxs-lookup"><span data-stu-id="e0845-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e0845-176">Linux</span><span class="sxs-lookup"><span data-stu-id="e0845-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="e0845-177">macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="e0845-178">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="e0845-179">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="e0845-180">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="e0845-181">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="e0845-182">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="e0845-183">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-183">Linux and macOS</span></span> |
| <span data-ttu-id="e0845-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(jenom nastavit)</span><span class="sxs-lookup"><span data-stu-id="e0845-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e0845-185">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-185">Linux and macOS</span></span> |
| <span data-ttu-id="e0845-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(jenom pro Get)</span><span class="sxs-lookup"><span data-stu-id="e0845-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="e0845-187">macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-187">macOS</span></span> |
| <span data-ttu-id="e0845-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType>(jenom nastavit)</span><span class="sxs-lookup"><span data-stu-id="e0845-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e0845-189">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="e0845-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="e0845-190">System.IO</span></span>

| <span data-ttu-id="e0845-191">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-191">Member</span></span> | <span data-ttu-id="e0845-192">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e0845-193">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e0845-194">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="e0845-195">System. IO. Pipes</span><span class="sxs-lookup"><span data-stu-id="e0845-195">System.IO.Pipes</span></span>

| <span data-ttu-id="e0845-196">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-196">Member</span></span> | <span data-ttu-id="e0845-197">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="e0845-198">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="e0845-199">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="e0845-200">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="e0845-201">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-201">Linux and macOS</span></span> |
| <span data-ttu-id="e0845-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType>(jenom nastavit)</span><span class="sxs-lookup"><span data-stu-id="e0845-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e0845-203">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="e0845-204">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="e0845-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="e0845-205">System.Media</span></span>

| <span data-ttu-id="e0845-206">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-206">Member</span></span> | <span data-ttu-id="e0845-207">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e0845-208">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="e0845-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="e0845-209">System.Net</span></span>

| <span data-ttu-id="e0845-210">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-210">Member</span></span> | <span data-ttu-id="e0845-211">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="e0845-212">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="e0845-213">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e0845-214">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e0845-215">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e0845-216">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e0845-217">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e0845-218">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e0845-219">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e0845-220">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e0845-221">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e0845-222">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="e0845-223">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="e0845-224">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e0845-225">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e0845-226">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e0845-227">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e0845-228">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="e0845-229">System .NET. NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="e0845-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="e0845-230">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-230">Member</span></span> | <span data-ttu-id="e0845-231">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="e0845-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="e0845-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="e0845-233">System .NET. Sockets</span><span class="sxs-lookup"><span data-stu-id="e0845-233">System.Net.Sockets</span></span>

| <span data-ttu-id="e0845-234">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-234">Member</span></span> | <span data-ttu-id="e0845-235">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="e0845-236">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="e0845-237">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="e0845-238">System .NET. WebSockets</span><span class="sxs-lookup"><span data-stu-id="e0845-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="e0845-239">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-239">Member</span></span> | <span data-ttu-id="e0845-240">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="e0845-241">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="e0845-242">System. Reflection</span><span class="sxs-lookup"><span data-stu-id="e0845-242">System.Reflection</span></span>

| <span data-ttu-id="e0845-243">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-243">Member</span></span> | <span data-ttu-id="e0845-244">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="e0845-245">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e0845-246">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e0845-247">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="e0845-248">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="e0845-249">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e0845-250">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="e0845-251">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="e0845-252">System. Runtime. CompilerServices</span><span class="sxs-lookup"><span data-stu-id="e0845-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="e0845-253">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-253">Member</span></span> | <span data-ttu-id="e0845-254">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="e0845-255">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="e0845-256">System. Runtime. InteropServices</span><span class="sxs-lookup"><span data-stu-id="e0845-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="e0845-257">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-257">Member</span></span> | <span data-ttu-id="e0845-258">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="e0845-259">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="e0845-260">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="e0845-261">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="e0845-262">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e0845-263">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="e0845-264">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="e0845-265">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="e0845-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="e0845-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="e0845-267">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-267">Member</span></span> | <span data-ttu-id="e0845-268">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="e0845-269">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="e0845-270">System. Security</span><span class="sxs-lookup"><span data-stu-id="e0845-270">System.Security</span></span>

| <span data-ttu-id="e0845-271">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-271">Member</span></span> | <span data-ttu-id="e0845-272">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="e0845-273">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="e0845-274">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="e0845-275">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="e0845-276">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="e0845-277">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="e0845-278">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="e0845-279">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="e0845-280">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="e0845-281">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="e0845-282">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="e0845-283">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="e0845-284">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="e0845-285">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="e0845-286">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="e0845-287">System. Security. Claims</span><span class="sxs-lookup"><span data-stu-id="e0845-287">System.Security.Claims</span></span>

| <span data-ttu-id="e0845-288">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-288">Member</span></span> | <span data-ttu-id="e0845-289">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor> | <span data-ttu-id="e0845-290">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e0845-291">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="e0845-292">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e0845-293">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e0845-294">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="e0845-295">System. Security. Cryptography</span><span class="sxs-lookup"><span data-stu-id="e0845-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="e0845-296">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-296">Member</span></span> | <span data-ttu-id="e0845-297">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e0845-298">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="e0845-299">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="e0845-300">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="e0845-301">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="e0845-302">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="e0845-303">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="e0845-304">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="e0845-305">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="e0845-306">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="e0845-307">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="e0845-308">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="e0845-309">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="e0845-310">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="e0845-311">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="e0845-312">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="e0845-313">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e0845-314">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="e0845-315">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="e0845-316">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="e0845-317">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="e0845-318">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e0845-319">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="e0845-320">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="e0845-321">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e0845-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="e0845-322">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="e0845-323">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="e0845-324">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e0845-325">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="e0845-326">System. Security. Cryptography. PKCS</span><span class="sxs-lookup"><span data-stu-id="e0845-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="e0845-327">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-327">Member</span></span> | <span data-ttu-id="e0845-328">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="e0845-329">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="e0845-330">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="e0845-331">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="e0845-332">System. Security. Cryptography. X509Certificates</span><span class="sxs-lookup"><span data-stu-id="e0845-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="e0845-333">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-333">Member</span></span> | <span data-ttu-id="e0845-334">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e0845-335">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="e0845-336">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e0845-337">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-337">All</span></span> |
| <span data-ttu-id="e0845-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType>(jenom nastavit)</span><span class="sxs-lookup"><span data-stu-id="e0845-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e0845-339">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="e0845-340">System. Security. Authentication. ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="e0845-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="e0845-341">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-341">Member</span></span> | <span data-ttu-id="e0845-342">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e0845-343">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="e0845-344">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="e0845-344">System.Security.Policy</span></span>

| <span data-ttu-id="e0845-345">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-345">Member</span></span> | <span data-ttu-id="e0845-346">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e0845-347">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="e0845-348">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="e0845-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="e0845-349">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-349">Member</span></span> | <span data-ttu-id="e0845-350">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="e0845-351">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="e0845-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="e0845-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="e0845-353">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-353">Member</span></span> | <span data-ttu-id="e0845-354">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="e0845-355">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="e0845-356">System. Threading</span><span class="sxs-lookup"><span data-stu-id="e0845-356">System.Threading</span></span>

| <span data-ttu-id="e0845-357">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-357">Member</span></span> | <span data-ttu-id="e0845-358">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e0845-359">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e0845-360">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="e0845-361">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="e0845-362">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="e0845-363">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="e0845-364">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="e0845-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="e0845-365">System.Xml</span></span>

| <span data-ttu-id="e0845-366">Člen</span><span class="sxs-lookup"><span data-stu-id="e0845-366">Member</span></span> | <span data-ttu-id="e0845-367">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e0845-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="e0845-368">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="e0845-369">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="e0845-370">Vše</span><span class="sxs-lookup"><span data-stu-id="e0845-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="e0845-371">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0845-371">See also</span></span>

- [<span data-ttu-id="e0845-372">Zásadní změny migrace z .NET Framework do .NET Core</span><span class="sxs-lookup"><span data-stu-id="e0845-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="e0845-373">Binární serializace v .NET Core</span><span class="sxs-lookup"><span data-stu-id="e0845-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="e0845-374">Analyzátor přenositelnosti .NET</span><span class="sxs-lookup"><span data-stu-id="e0845-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
