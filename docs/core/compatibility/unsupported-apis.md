---
title: Nepodporovaná rozhraní API v .NET Core
titleSuffix: ''
description: Seznamte se s rozhraními API z .NET Framework, která vždy vyvolají výjimku pro .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: c4b94321d30cacd90d5c2ee23c258681683a6faa
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092964"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="b4798-103">Rozhraní API, která vždy vyvolávají výjimky v .NET Core</span><span class="sxs-lookup"><span data-stu-id="b4798-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="b4798-104">Následující rozhraní API budou vždycky vyvolávat <xref:System.PlatformNotSupportedException> v .NET Core ve všech nebo v podmnožině platforem.</span><span class="sxs-lookup"><span data-stu-id="b4798-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="b4798-105">Tento článek uspořádá ovlivněné členy rozhraní API podle oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b4798-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="b4798-106">Tento článek je nedokončený.</span><span class="sxs-lookup"><span data-stu-id="b4798-106">This article is a work-in-progress.</span></span> <span data-ttu-id="b4798-107">Nejedná se o úplný seznam rozhraní API, která vyvolávají výjimky v rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b4798-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="b4798-108">Tento článek nezahrnuje implementace explicitního rozhraní pro binární serializaci, která se vyvolává v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b4798-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="b4798-109">Další informace najdete v tématu [binární serializace v .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="b4798-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="b4798-110">Systémový</span><span class="sxs-lookup"><span data-stu-id="b4798-110">System</span></span>

| <span data-ttu-id="b4798-111">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-111">Member</span></span> | <span data-ttu-id="b4798-112">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-113">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="b4798-114">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="b4798-115">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="b4798-116">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-117">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="b4798-118">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="b4798-119">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="b4798-120">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-121">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="b4798-122">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="b4798-123">System. CodeDom. Compiler</span><span class="sxs-lookup"><span data-stu-id="b4798-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="b4798-124">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-124">Member</span></span> | <span data-ttu-id="b4798-125">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-126">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-127">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-128">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="b4798-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="b4798-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="b4798-130">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-130">Member</span></span> | <span data-ttu-id="b4798-131">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-132">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-133">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="b4798-134">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="b4798-135">System. Configuration</span><span class="sxs-lookup"><span data-stu-id="b4798-135">System.Configuration</span></span>

| <span data-ttu-id="b4798-136">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-136">Member</span></span> | <span data-ttu-id="b4798-137">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="b4798-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (všichni členové)</span><span class="sxs-lookup"><span data-stu-id="b4798-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="b4798-139">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="b4798-140">System. Console</span><span class="sxs-lookup"><span data-stu-id="b4798-140">System.Console</span></span>

| <span data-ttu-id="b4798-141">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-141">Member</span></span> | <span data-ttu-id="b4798-142">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="b4798-143">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-143">Linux and macOS</span></span> |
| <span data-ttu-id="b4798-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="b4798-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4798-145">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-145">Linux and macOS</span></span> |
| <span data-ttu-id="b4798-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="b4798-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4798-147">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-147">Linux and macOS</span></span> |
| <span data-ttu-id="b4798-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="b4798-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4798-149">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-149">Linux and macOS</span></span> |
| <span data-ttu-id="b4798-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (jenom pro Get)</span><span class="sxs-lookup"><span data-stu-id="b4798-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="b4798-151">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-152">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-153">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-154">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-154">Linux and macOS</span></span> |
| <span data-ttu-id="b4798-155"><xref:System.Console.Title?displayProperty=nameWithType> (jenom pro Get)</span><span class="sxs-lookup"><span data-stu-id="b4798-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="b4798-156">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-156">Linux and macOS</span></span> |
| <span data-ttu-id="b4798-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="b4798-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4798-158">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-158">Linux and macOS</span></span> |
| <span data-ttu-id="b4798-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="b4798-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4798-160">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-160">Linux and macOS</span></span> |
| <span data-ttu-id="b4798-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="b4798-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4798-162">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-162">Linux and macOS</span></span> |
| <span data-ttu-id="b4798-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="b4798-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4798-164">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="b4798-165">System. data. Common</span><span class="sxs-lookup"><span data-stu-id="b4798-165">System.Data.Common</span></span>

| <span data-ttu-id="b4798-166">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-166">Member</span></span> | <span data-ttu-id="b4798-167">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="b4798-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (vyvolá <xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="b4798-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="b4798-169">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="b4798-170">System. Diagnostics. Process</span><span class="sxs-lookup"><span data-stu-id="b4798-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="b4798-171">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-171">Member</span></span> | <span data-ttu-id="b4798-172">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="b4798-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="b4798-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4798-174">Linux</span><span class="sxs-lookup"><span data-stu-id="b4798-174">Linux</span></span> |
| <span data-ttu-id="b4798-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="b4798-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4798-176">Linux</span><span class="sxs-lookup"><span data-stu-id="b4798-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="b4798-177">macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="b4798-178">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-179">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="b4798-180">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="b4798-181">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="b4798-182">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="b4798-183">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-183">Linux and macOS</span></span> |
| <span data-ttu-id="b4798-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="b4798-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4798-185">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-185">Linux and macOS</span></span> |
| <span data-ttu-id="b4798-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (jenom pro Get)</span><span class="sxs-lookup"><span data-stu-id="b4798-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="b4798-187">macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-187">macOS</span></span> |
| <span data-ttu-id="b4798-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="b4798-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4798-189">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="b4798-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="b4798-190">System.IO</span></span>

| <span data-ttu-id="b4798-191">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-191">Member</span></span> | <span data-ttu-id="b4798-192">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-193">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-194">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="b4798-195">System. IO. Pipes</span><span class="sxs-lookup"><span data-stu-id="b4798-195">System.IO.Pipes</span></span>

| <span data-ttu-id="b4798-196">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-196">Member</span></span> | <span data-ttu-id="b4798-197">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="b4798-198">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="b4798-199">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="b4798-200">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="b4798-201">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-201">Linux and macOS</span></span> |
| <span data-ttu-id="b4798-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="b4798-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4798-203">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="b4798-204">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="b4798-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="b4798-205">System.Media</span></span>

| <span data-ttu-id="b4798-206">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-206">Member</span></span> | <span data-ttu-id="b4798-207">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-208">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="b4798-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="b4798-209">System.Net</span></span>

| <span data-ttu-id="b4798-210">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-210">Member</span></span> | <span data-ttu-id="b4798-211">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="b4798-212">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="b4798-213">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-214">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-215">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-216">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-217">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-218">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-219">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-220">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-221">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-222">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="b4798-223">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-224">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-225">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-226">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-227">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-228">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="b4798-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="b4798-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="b4798-230">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-230">Member</span></span> | <span data-ttu-id="b4798-231">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="b4798-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="b4798-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="b4798-233">System.Net.Sockets</span></span>

| <span data-ttu-id="b4798-234">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-234">Member</span></span> | <span data-ttu-id="b4798-235">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)?displayProperty=nameWithType> | <span data-ttu-id="b4798-236">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="b4798-237">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="b4798-238">System .NET. WebSockets</span><span class="sxs-lookup"><span data-stu-id="b4798-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="b4798-239">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-239">Member</span></span> | <span data-ttu-id="b4798-240">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="b4798-241">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="b4798-242">System. Reflection</span><span class="sxs-lookup"><span data-stu-id="b4798-242">System.Reflection</span></span>

| <span data-ttu-id="b4798-243">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-243">Member</span></span> | <span data-ttu-id="b4798-244">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-245">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b4798-246">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-247">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="b4798-248">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b4798-249">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-250">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="b4798-251">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="b4798-252">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="b4798-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="b4798-253">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-253">Member</span></span> | <span data-ttu-id="b4798-254">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="b4798-255">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="b4798-256">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="b4798-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="b4798-257">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-257">Member</span></span> | <span data-ttu-id="b4798-258">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="b4798-259">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="b4798-260">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="b4798-261">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="b4798-262">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b4798-263">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="b4798-264">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="b4798-265">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="b4798-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="b4798-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="b4798-267">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-267">Member</span></span> | <span data-ttu-id="b4798-268">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="b4798-269">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="b4798-270">System. Security</span><span class="sxs-lookup"><span data-stu-id="b4798-270">System.Security</span></span>

| <span data-ttu-id="b4798-271">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-271">Member</span></span> | <span data-ttu-id="b4798-272">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="b4798-273">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="b4798-274">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="b4798-275">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="b4798-276">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="b4798-277">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="b4798-278">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="b4798-279">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="b4798-280">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="b4798-281">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="b4798-282">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="b4798-283">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="b4798-284">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="b4798-285">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="b4798-286">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="b4798-287">System. Security. Claims</span><span class="sxs-lookup"><span data-stu-id="b4798-287">System.Security.Claims</span></span>

| <span data-ttu-id="b4798-288">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-288">Member</span></span> | <span data-ttu-id="b4798-289">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | <span data-ttu-id="b4798-290">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-291">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | <span data-ttu-id="b4798-292">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-293">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-294">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="b4798-295">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="b4798-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="b4798-296">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-296">Member</span></span> | <span data-ttu-id="b4798-297">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b4798-298">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-299">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="b4798-300">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="b4798-301">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="b4798-302">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="b4798-303">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="b4798-304">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="b4798-305">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="b4798-306">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="b4798-307">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="b4798-308">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="b4798-309">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="b4798-310">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="b4798-311">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="b4798-312">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="b4798-313">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b4798-314">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-315">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-316">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-317">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="b4798-318">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b4798-319">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-320">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-321">Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="b4798-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-322">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-323">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="b4798-324">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b4798-325">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="b4798-326">System. Security. Cryptography. PKCS</span><span class="sxs-lookup"><span data-stu-id="b4798-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="b4798-327">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-327">Member</span></span> | <span data-ttu-id="b4798-328">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | <span data-ttu-id="b4798-329">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="b4798-330">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="b4798-331">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="b4798-332">System. Security. Cryptography. X509Certificates</span><span class="sxs-lookup"><span data-stu-id="b4798-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="b4798-333">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-333">Member</span></span> | <span data-ttu-id="b4798-334">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-335">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-336">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-337">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-337">All</span></span> |
| <span data-ttu-id="b4798-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (pouze nastavit)</span><span class="sxs-lookup"><span data-stu-id="b4798-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4798-339">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="b4798-340">System. Security. Authentication. ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="b4798-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="b4798-341">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-341">Member</span></span> | <span data-ttu-id="b4798-342">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-343">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="b4798-344">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="b4798-344">System.Security.Policy</span></span>

| <span data-ttu-id="b4798-345">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-345">Member</span></span> | <span data-ttu-id="b4798-346">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-347">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="b4798-348">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="b4798-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="b4798-349">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-349">Member</span></span> | <span data-ttu-id="b4798-350">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-351">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="b4798-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="b4798-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="b4798-353">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-353">Member</span></span> | <span data-ttu-id="b4798-354">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-355">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="b4798-356">System. Threading</span><span class="sxs-lookup"><span data-stu-id="b4798-356">System.Threading</span></span>

| <span data-ttu-id="b4798-357">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-357">Member</span></span> | <span data-ttu-id="b4798-358">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-359">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4798-360">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="b4798-361">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="b4798-362">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="b4798-363">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="b4798-364">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="b4798-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="b4798-365">System.Xml</span></span>

| <span data-ttu-id="b4798-366">Člen</span><span class="sxs-lookup"><span data-stu-id="b4798-366">Member</span></span> | <span data-ttu-id="b4798-367">Platformy, které vyvolávají výjimku</span><span class="sxs-lookup"><span data-stu-id="b4798-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="b4798-368">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="b4798-369">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="b4798-370">Všechny</span><span class="sxs-lookup"><span data-stu-id="b4798-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="b4798-371">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4798-371">See also</span></span>

- [<span data-ttu-id="b4798-372">Zásadní změny migrace z .NET Framework do .NET Core</span><span class="sxs-lookup"><span data-stu-id="b4798-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="b4798-373">Binární serializace v .NET Core</span><span class="sxs-lookup"><span data-stu-id="b4798-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="b4798-374">Analyzátor přenositelnosti .NET</span><span class="sxs-lookup"><span data-stu-id="b4798-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
