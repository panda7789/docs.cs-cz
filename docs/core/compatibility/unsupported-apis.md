---
title: Nepodporovaná rozhraní API v .NET Core
description: Seznamte se s rozhraními API z .NET Framework, která vždy vyvolají výjimku pro .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: f27aeca31226a95dacf100813762eedb56876fbd
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936977"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="e660d-103">Rozhraní API, která vždy vyvolávají výjimky v .NET Core</span><span class="sxs-lookup"><span data-stu-id="e660d-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="e660d-104">Následující rozhraní API budou vždycky vyvolávat <xref:System.PlatformNotSupportedException> v .NET Core ve všech nebo v podmnožině platforem.</span><span class="sxs-lookup"><span data-stu-id="e660d-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="e660d-105">Tento článek uspořádá ovlivněné členy rozhraní API podle oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e660d-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="e660d-106">Tento článek je nedokončený.</span><span class="sxs-lookup"><span data-stu-id="e660d-106">This article is a work-in-progress.</span></span> <span data-ttu-id="e660d-107">Nejedná se o úplný seznam rozhraní API, která vyvolávají výjimky v rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e660d-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="e660d-108">Tento článek nezahrnuje implementace explicitního rozhraní pro binární serializaci, která se vyvolává v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e660d-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="e660d-109">Další informace najdete v tématu [binární serializace v .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="e660d-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="e660d-110">Systém</span><span class="sxs-lookup"><span data-stu-id="e660d-110">System</span></span>

| <span data-ttu-id="e660d-111">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-111">Member</span></span> | <span data-ttu-id="e660d-112">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-113">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="e660d-114">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="e660d-115">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="e660d-116">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-117">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="e660d-118">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="e660d-119">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="e660d-120">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-121">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="e660d-122">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="e660d-123">System. CodeDom. Compiler</span><span class="sxs-lookup"><span data-stu-id="e660d-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="e660d-124">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-124">Member</span></span> | <span data-ttu-id="e660d-125">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-126">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-127">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-128">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="e660d-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="e660d-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="e660d-130">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-130">Member</span></span> | <span data-ttu-id="e660d-131">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-132">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-133">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="e660d-134">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="e660d-135">System. Configuration</span><span class="sxs-lookup"><span data-stu-id="e660d-135">System.Configuration</span></span>

| <span data-ttu-id="e660d-136">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-136">Member</span></span> | <span data-ttu-id="e660d-137">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="e660d-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (všichni členové)</span><span class="sxs-lookup"><span data-stu-id="e660d-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="e660d-139">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="e660d-140">System. Console</span><span class="sxs-lookup"><span data-stu-id="e660d-140">System.Console</span></span>

| <span data-ttu-id="e660d-141">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-141">Member</span></span> | <span data-ttu-id="e660d-142">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="e660d-143">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-143">Linux and macOS</span></span> |
| <span data-ttu-id="e660d-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="e660d-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e660d-145">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-145">Linux and macOS</span></span> |
| <span data-ttu-id="e660d-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="e660d-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e660d-147">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-147">Linux and macOS</span></span> |
| <span data-ttu-id="e660d-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="e660d-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e660d-149">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-149">Linux and macOS</span></span> |
| <span data-ttu-id="e660d-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (jenom pro Get)</span><span class="sxs-lookup"><span data-stu-id="e660d-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="e660d-151">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-152">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-153">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-154">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-154">Linux and macOS</span></span> |
| <span data-ttu-id="e660d-155"><xref:System.Console.Title?displayProperty=nameWithType> (jenom pro Get)</span><span class="sxs-lookup"><span data-stu-id="e660d-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="e660d-156">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-156">Linux and macOS</span></span> |
| <span data-ttu-id="e660d-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="e660d-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e660d-158">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-158">Linux and macOS</span></span> |
| <span data-ttu-id="e660d-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="e660d-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e660d-160">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-160">Linux and macOS</span></span> |
| <span data-ttu-id="e660d-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="e660d-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e660d-162">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-162">Linux and macOS</span></span> |
| <span data-ttu-id="e660d-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="e660d-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e660d-164">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="e660d-165">System. data. Common</span><span class="sxs-lookup"><span data-stu-id="e660d-165">System.Data.Common</span></span>

| <span data-ttu-id="e660d-166">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-166">Member</span></span> | <span data-ttu-id="e660d-167">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="e660d-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (vyvolá <xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="e660d-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="e660d-169">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="e660d-170">System. Diagnostics. Process</span><span class="sxs-lookup"><span data-stu-id="e660d-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="e660d-171">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-171">Member</span></span> | <span data-ttu-id="e660d-172">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="e660d-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="e660d-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e660d-174">Linux</span><span class="sxs-lookup"><span data-stu-id="e660d-174">Linux</span></span> |
| <span data-ttu-id="e660d-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="e660d-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e660d-176">Linux</span><span class="sxs-lookup"><span data-stu-id="e660d-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="e660d-177">macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="e660d-178">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-179">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="e660d-180">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="e660d-181">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="e660d-182">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="e660d-183">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-183">Linux and macOS</span></span> |
| <span data-ttu-id="e660d-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="e660d-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e660d-185">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-185">Linux and macOS</span></span> |
| <span data-ttu-id="e660d-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (jenom pro Get)</span><span class="sxs-lookup"><span data-stu-id="e660d-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="e660d-187">macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-187">macOS</span></span> |
| <span data-ttu-id="e660d-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="e660d-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e660d-189">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="e660d-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="e660d-190">System.IO</span></span>

| <span data-ttu-id="e660d-191">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-191">Member</span></span> | <span data-ttu-id="e660d-192">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-193">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-194">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="e660d-195">System. IO. Pipes</span><span class="sxs-lookup"><span data-stu-id="e660d-195">System.IO.Pipes</span></span>

| <span data-ttu-id="e660d-196">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-196">Member</span></span> | <span data-ttu-id="e660d-197">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="e660d-198">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="e660d-199">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="e660d-200">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="e660d-201">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-201">Linux and macOS</span></span> |
| <span data-ttu-id="e660d-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="e660d-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e660d-203">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="e660d-204">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="e660d-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="e660d-205">System.Media</span></span>

| <span data-ttu-id="e660d-206">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-206">Member</span></span> | <span data-ttu-id="e660d-207">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-208">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="e660d-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="e660d-209">System.Net</span></span>

| <span data-ttu-id="e660d-210">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-210">Member</span></span> | <span data-ttu-id="e660d-211">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="e660d-212">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="e660d-213">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-214">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-215">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-216">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-217">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-218">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-219">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-220">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-221">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-222">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="e660d-223">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-224">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-225">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-226">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-227">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-228">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="e660d-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="e660d-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="e660d-230">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-230">Member</span></span> | <span data-ttu-id="e660d-231">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="e660d-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="e660d-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="e660d-233">System.Net.Sockets</span></span>

| <span data-ttu-id="e660d-234">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-234">Member</span></span> | <span data-ttu-id="e660d-235">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="e660d-236">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-236">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="e660d-237">System .NET. WebSockets</span><span class="sxs-lookup"><span data-stu-id="e660d-237">System.Net.WebSockets</span></span>

| <span data-ttu-id="e660d-238">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-238">Member</span></span> | <span data-ttu-id="e660d-239">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-239">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="e660d-240">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-240">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="e660d-241">System. Reflection</span><span class="sxs-lookup"><span data-stu-id="e660d-241">System.Reflection</span></span>

| <span data-ttu-id="e660d-242">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-242">Member</span></span> | <span data-ttu-id="e660d-243">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-243">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-244">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-244">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e660d-245">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-245">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-246">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="e660d-247">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-247">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e660d-248">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-249">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="e660d-250">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-250">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="e660d-251">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="e660d-251">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="e660d-252">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-252">Member</span></span> | <span data-ttu-id="e660d-253">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-253">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="e660d-254">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-254">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="e660d-255">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="e660d-255">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="e660d-256">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-256">Member</span></span> | <span data-ttu-id="e660d-257">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-257">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="e660d-258">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-258">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="e660d-259">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="e660d-260">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="e660d-261">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-261">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e660d-262">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-262">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="e660d-263">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="e660d-264">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-264">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="e660d-265">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="e660d-265">System.Runtime.Serialization</span></span>

| <span data-ttu-id="e660d-266">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-266">Member</span></span> | <span data-ttu-id="e660d-267">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-267">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="e660d-268">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-268">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="e660d-269">System. Security</span><span class="sxs-lookup"><span data-stu-id="e660d-269">System.Security</span></span>

| <span data-ttu-id="e660d-270">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-270">Member</span></span> | <span data-ttu-id="e660d-271">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-271">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="e660d-272">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-272">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="e660d-273">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-273">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="e660d-274">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-274">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="e660d-275">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-275">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="e660d-276">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-276">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="e660d-277">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-277">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="e660d-278">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-278">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="e660d-279">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-279">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="e660d-280">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="e660d-281">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-281">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="e660d-282">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-282">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="e660d-283">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-283">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="e660d-284">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="e660d-285">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-285">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="e660d-286">System. Security. Claims</span><span class="sxs-lookup"><span data-stu-id="e660d-286">System.Security.Claims</span></span>

| <span data-ttu-id="e660d-287">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-287">Member</span></span> | <span data-ttu-id="e660d-288">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-288">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | <span data-ttu-id="e660d-289">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-289">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-290">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | <span data-ttu-id="e660d-291">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-292">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-293">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-293">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="e660d-294">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="e660d-294">System.Security.Cryptography</span></span>

| <span data-ttu-id="e660d-295">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-295">Member</span></span> | <span data-ttu-id="e660d-296">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-296">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e660d-297">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-297">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-298">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-298">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="e660d-299">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="e660d-300">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="e660d-301">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="e660d-302">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="e660d-303">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="e660d-304">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="e660d-305">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="e660d-306">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="e660d-307">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="e660d-308">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="e660d-309">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="e660d-310">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="e660d-311">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-311">All</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e660d-312">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="e660d-313">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e660d-314">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-315">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-316">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-317">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="e660d-318">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e660d-319">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-320">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-321">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="e660d-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-322">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-323">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="e660d-324">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="e660d-325">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="e660d-326">System. Security. Cryptography. PKCS</span><span class="sxs-lookup"><span data-stu-id="e660d-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="e660d-327">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-327">Member</span></span> | <span data-ttu-id="e660d-328">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | <span data-ttu-id="e660d-329">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="e660d-330">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="e660d-331">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="e660d-332">System. Security. Cryptography. X509Certificates</span><span class="sxs-lookup"><span data-stu-id="e660d-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="e660d-333">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-333">Member</span></span> | <span data-ttu-id="e660d-334">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-335">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-336">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-337">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-337">All</span></span> |
| <span data-ttu-id="e660d-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="e660d-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="e660d-339">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="e660d-340">System. Security. Authentication. ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="e660d-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="e660d-341">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-341">Member</span></span> | <span data-ttu-id="e660d-342">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-343">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="e660d-344">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="e660d-344">System.Security.Policy</span></span>

| <span data-ttu-id="e660d-345">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-345">Member</span></span> | <span data-ttu-id="e660d-346">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-347">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="e660d-348">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="e660d-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="e660d-349">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-349">Member</span></span> | <span data-ttu-id="e660d-350">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-351">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="e660d-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="e660d-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="e660d-353">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-353">Member</span></span> | <span data-ttu-id="e660d-354">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-355">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="e660d-356">System. Threading</span><span class="sxs-lookup"><span data-stu-id="e660d-356">System.Threading</span></span>

| <span data-ttu-id="e660d-357">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-357">Member</span></span> | <span data-ttu-id="e660d-358">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-359">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="e660d-360">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="e660d-361">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="e660d-362">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="e660d-363">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="e660d-364">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="e660d-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="e660d-365">System.Xml</span></span>

| <span data-ttu-id="e660d-366">Člen</span><span class="sxs-lookup"><span data-stu-id="e660d-366">Member</span></span> | <span data-ttu-id="e660d-367">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="e660d-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="e660d-368">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="e660d-369">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="e660d-370">Všechny</span><span class="sxs-lookup"><span data-stu-id="e660d-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="e660d-371">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e660d-371">See also</span></span>

- [<span data-ttu-id="e660d-372">Zásadní změny migrace z .NET Framework do .NET Core</span><span class="sxs-lookup"><span data-stu-id="e660d-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="e660d-373">Binární serializace v .NET Core</span><span class="sxs-lookup"><span data-stu-id="e660d-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="e660d-374">Analyzátor přenositelnosti .NET</span><span class="sxs-lookup"><span data-stu-id="e660d-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
