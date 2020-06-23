---
title: Třída Logging (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Logging
- System.Net.Logging.Associate
- System.Net.Logging.Enter
- System.Net.Logging.Exception
- System.Net.Logging.Exit
- System.Net.Logging.get_Http
- System.Net.Logging.get_On
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ad85fdd41252ed147eb5fe1a9db029db046d720c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990334"
---
# <a name="logging-class"></a><span data-ttu-id="91461-102">Logging – třída</span><span class="sxs-lookup"><span data-stu-id="91461-102">Logging class</span></span>

<span data-ttu-id="91461-103">Poskytuje funkce protokolování trasování.</span><span class="sxs-lookup"><span data-stu-id="91461-103">Provides trace logging functionality.</span></span>

```csharp
internal class Logging
```

> [!WARNING]
> <span data-ttu-id="91461-104">Tato třída je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="91461-104">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="91461-105">Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="91461-105">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="associate-method"></a><span data-ttu-id="91461-106">Přidružte metodu</span><span class="sxs-lookup"><span data-stu-id="91461-106">Associate method</span></span>

<span data-ttu-id="91461-107">Protokoluje informace, ke kterým jsou přidruženy dva objekty.</span><span class="sxs-lookup"><span data-stu-id="91461-107">Logs information that two objects are associated with each other.</span></span>

```csharp
internal static void Associate(TraceSource traceSource, object objA, object objB)
```

### <a name="parameters"></a><span data-ttu-id="91461-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="91461-108">Parameters</span></span>

- <span data-ttu-id="91461-109">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="91461-109">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="91461-110">Zdroj trasování pro zaprotokolování události do protokolu.</span><span class="sxs-lookup"><span data-stu-id="91461-110">The trace source to log the event to.</span></span>

- <span data-ttu-id="91461-111">`objA` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="91461-111">`objA` <xref:System.Object></span></span>

  <span data-ttu-id="91461-112">Objekt, ke kterému se má přidružit `objB` .</span><span class="sxs-lookup"><span data-stu-id="91461-112">The object to associate with `objB`.</span></span>

- <span data-ttu-id="91461-113">`objB` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="91461-113">`objB` <xref:System.Object></span></span>

  <span data-ttu-id="91461-114">Objekt, ke kterému se má přidružit `objA` .</span><span class="sxs-lookup"><span data-stu-id="91461-114">The object to associate with `objA`.</span></span>

## <a name="entertracesource-object-string-string-method"></a><span data-ttu-id="91461-115">ENTER (TraceSource, Object, String, String) – metoda</span><span class="sxs-lookup"><span data-stu-id="91461-115">Enter(TraceSource, object, string, string) method</span></span>

<span data-ttu-id="91461-116">Zapíše vstup do metody.</span><span class="sxs-lookup"><span data-stu-id="91461-116">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, string param)
```

### <a name="parameters"></a><span data-ttu-id="91461-117">Parametry</span><span class="sxs-lookup"><span data-stu-id="91461-117">Parameters</span></span>

- <span data-ttu-id="91461-118">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="91461-118">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="91461-119">Zdroj trasování pro zaprotokolování události do protokolu.</span><span class="sxs-lookup"><span data-stu-id="91461-119">The trace source to log the event to.</span></span>

- <span data-ttu-id="91461-120">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="91461-120">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="91461-121">Objekt, na kterém byla metoda volána.</span><span class="sxs-lookup"><span data-stu-id="91461-121">The object that the method was called on.</span></span>

- <span data-ttu-id="91461-122">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-122">`method` <xref:System.String></span></span>

  <span data-ttu-id="91461-123">Metoda, která je zadávána.</span><span class="sxs-lookup"><span data-stu-id="91461-123">The method that is being entered.</span></span>

- <span data-ttu-id="91461-124">`param` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-124">`param` <xref:System.String></span></span>

  <span data-ttu-id="91461-125">Parametry, které byly předány metodě.</span><span class="sxs-lookup"><span data-stu-id="91461-125">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-object-string-object-method"></a><span data-ttu-id="91461-126">ENTER (TraceSource; Object; String; objekt) – metoda</span><span class="sxs-lookup"><span data-stu-id="91461-126">Enter(TraceSource, object, string, object) method</span></span>

<span data-ttu-id="91461-127">Zapíše vstup do metody.</span><span class="sxs-lookup"><span data-stu-id="91461-127">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, object paramObject)
```

### <a name="parameters"></a><span data-ttu-id="91461-128">Parametry</span><span class="sxs-lookup"><span data-stu-id="91461-128">Parameters</span></span>

- <span data-ttu-id="91461-129">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="91461-129">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="91461-130">Zdroj trasování pro zaprotokolování události do protokolu.</span><span class="sxs-lookup"><span data-stu-id="91461-130">The trace source to log the event to.</span></span>

- <span data-ttu-id="91461-131">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="91461-131">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="91461-132">Objekt, na kterém byla metoda volána.</span><span class="sxs-lookup"><span data-stu-id="91461-132">The object that the method was called on.</span></span>

- <span data-ttu-id="91461-133">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-133">`method` <xref:System.String></span></span>

  <span data-ttu-id="91461-134">Metoda, která je zadávána.</span><span class="sxs-lookup"><span data-stu-id="91461-134">The method that is being entered.</span></span>

- <span data-ttu-id="91461-135">`paramObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="91461-135">`paramObject` <xref:System.Object></span></span>

  <span data-ttu-id="91461-136">Parametry, které byly předány metodě.</span><span class="sxs-lookup"><span data-stu-id="91461-136">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-string-method"></a><span data-ttu-id="91461-137">ENTER (TraceSource, String, String, String) – metoda</span><span class="sxs-lookup"><span data-stu-id="91461-137">Enter(TraceSource, string, string, string) method</span></span>

<span data-ttu-id="91461-138">Zapíše vstup do metody.</span><span class="sxs-lookup"><span data-stu-id="91461-138">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, string param)
```

### <a name="parameters"></a><span data-ttu-id="91461-139">Parametry</span><span class="sxs-lookup"><span data-stu-id="91461-139">Parameters</span></span>

- <span data-ttu-id="91461-140">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="91461-140">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="91461-141">Zdroj trasování pro zaprotokolování události do protokolu.</span><span class="sxs-lookup"><span data-stu-id="91461-141">The trace source to log the event to.</span></span>

- <span data-ttu-id="91461-142">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-142">`obj` <xref:System.String></span></span>

  <span data-ttu-id="91461-143">Objekt, na kterém byla metoda volána.</span><span class="sxs-lookup"><span data-stu-id="91461-143">The object that the method was called on.</span></span>

- <span data-ttu-id="91461-144">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-144">`method` <xref:System.String></span></span>

  <span data-ttu-id="91461-145">Metoda, která je zadávána.</span><span class="sxs-lookup"><span data-stu-id="91461-145">The method that is being entered.</span></span>

- <span data-ttu-id="91461-146">`param` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-146">`param` <xref:System.String></span></span>

  <span data-ttu-id="91461-147">Parametry, které byly předány metodě.</span><span class="sxs-lookup"><span data-stu-id="91461-147">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-object-method"></a><span data-ttu-id="91461-148">ENTER (TraceSource, String, String, objekt) – metoda</span><span class="sxs-lookup"><span data-stu-id="91461-148">Enter(TraceSource, string, string, object) method</span></span>

<span data-ttu-id="91461-149">Zapíše vstup do metody.</span><span class="sxs-lookup"><span data-stu-id="91461-149">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, object paramObject)
```

### <a name="parameters"></a><span data-ttu-id="91461-150">Parametry</span><span class="sxs-lookup"><span data-stu-id="91461-150">Parameters</span></span>

- <span data-ttu-id="91461-151">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="91461-151">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="91461-152">Zdroj trasování pro zaprotokolování události do protokolu.</span><span class="sxs-lookup"><span data-stu-id="91461-152">The trace source to log the event to.</span></span>

- <span data-ttu-id="91461-153">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-153">`obj` <xref:System.String></span></span>

  <span data-ttu-id="91461-154">Objekt, na kterém byla metoda volána.</span><span class="sxs-lookup"><span data-stu-id="91461-154">The object that the method was called on.</span></span>

- <span data-ttu-id="91461-155">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-155">`method` <xref:System.String></span></span>

  <span data-ttu-id="91461-156">Metoda, která je zadávána.</span><span class="sxs-lookup"><span data-stu-id="91461-156">The method that is being entered.</span></span>

- <span data-ttu-id="91461-157">`paramObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="91461-157">`paramObject` <xref:System.Object></span></span>

  <span data-ttu-id="91461-158">Parametry, které byly předány metodě.</span><span class="sxs-lookup"><span data-stu-id="91461-158">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-method"></a><span data-ttu-id="91461-159">ENTER (TraceSource, String, String) – metoda</span><span class="sxs-lookup"><span data-stu-id="91461-159">Enter(TraceSource, string, string) method</span></span>

<span data-ttu-id="91461-160">Zapíše vstup do metody.</span><span class="sxs-lookup"><span data-stu-id="91461-160">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a><span data-ttu-id="91461-161">Parametry</span><span class="sxs-lookup"><span data-stu-id="91461-161">Parameters</span></span>

- <span data-ttu-id="91461-162">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="91461-162">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="91461-163">Zdroj trasování pro zaprotokolování události do protokolu.</span><span class="sxs-lookup"><span data-stu-id="91461-163">The trace source to log the event to.</span></span>

- <span data-ttu-id="91461-164">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-164">`method` <xref:System.String></span></span>

  <span data-ttu-id="91461-165">Metoda, která je zadávána.</span><span class="sxs-lookup"><span data-stu-id="91461-165">The method that is being entered.</span></span>

- <span data-ttu-id="91461-166">`parameters` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-166">`parameters` <xref:System.String></span></span>

  <span data-ttu-id="91461-167">Parametry, které byly předány metodě.</span><span class="sxs-lookup"><span data-stu-id="91461-167">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-method"></a><span data-ttu-id="91461-168">Enter – Metoda (TraceSource, String)</span><span class="sxs-lookup"><span data-stu-id="91461-168">Enter(TraceSource, string) method</span></span>

<span data-ttu-id="91461-169">Zapíše vstup do metody.</span><span class="sxs-lookup"><span data-stu-id="91461-169">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string msg)
```

### <a name="parameters"></a><span data-ttu-id="91461-170">Parametry</span><span class="sxs-lookup"><span data-stu-id="91461-170">Parameters</span></span>

- <span data-ttu-id="91461-171">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="91461-171">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="91461-172">Zdroj trasování pro zaprotokolování události do protokolu.</span><span class="sxs-lookup"><span data-stu-id="91461-172">The trace source to log the event to.</span></span>

- <span data-ttu-id="91461-173">`msg` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-173">`msg` <xref:System.String></span></span>

  <span data-ttu-id="91461-174">Úvodní zpráva, která se má přihlásit ke zdroji trasování.</span><span class="sxs-lookup"><span data-stu-id="91461-174">The entrance message to log to the trace source.</span></span>

## <a name="exception-method"></a><span data-ttu-id="91461-175">Exception – metoda</span><span class="sxs-lookup"><span data-stu-id="91461-175">Exception method</span></span>

<span data-ttu-id="91461-176">Zaznamená výjimku a obnoví odsazení.</span><span class="sxs-lookup"><span data-stu-id="91461-176">Logs an exception and restores indentation.</span></span>

```csharp
internal static void Exception(TraceSource traceSource, object obj, string method, Exception e)
```

### <a name="parameters"></a><span data-ttu-id="91461-177">Parametry</span><span class="sxs-lookup"><span data-stu-id="91461-177">Parameters</span></span>

- <span data-ttu-id="91461-178">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="91461-178">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="91461-179">Zdroj trasování pro zaprotokolování události do protokolu.</span><span class="sxs-lookup"><span data-stu-id="91461-179">The trace source to log the event to.</span></span>

- <span data-ttu-id="91461-180">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="91461-180">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="91461-181">Objekt, na kterém byla volána metoda, která vyvolala výjimku.</span><span class="sxs-lookup"><span data-stu-id="91461-181">The object that the method that threw an exception was called on.</span></span>

- <span data-ttu-id="91461-182">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-182">`method` <xref:System.String></span></span>

  <span data-ttu-id="91461-183">Metoda, která vyvolala výjimku.</span><span class="sxs-lookup"><span data-stu-id="91461-183">The method that threw the exception.</span></span>

- <span data-ttu-id="91461-184">`e` <xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="91461-184">`e` <xref:System.Exception></span></span>

  <span data-ttu-id="91461-185">Výjimka, která byla vyvolána.</span><span class="sxs-lookup"><span data-stu-id="91461-185">The exception that was thrown.</span></span>

## <a name="exittracesource-object-string-object-method"></a><span data-ttu-id="91461-186">Exit (TraceSource, objekt, String, objekt) – metoda</span><span class="sxs-lookup"><span data-stu-id="91461-186">Exit(TraceSource, object, string, object) method</span></span>

<span data-ttu-id="91461-187">Protokoly se ukončí od funkce.</span><span class="sxs-lookup"><span data-stu-id="91461-187">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, object retObject)
```

### <a name="parameters"></a><span data-ttu-id="91461-188">Parametry</span><span class="sxs-lookup"><span data-stu-id="91461-188">Parameters</span></span>

- <span data-ttu-id="91461-189">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="91461-189">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="91461-190">Zdroj trasování pro zaprotokolování události do protokolu.</span><span class="sxs-lookup"><span data-stu-id="91461-190">The trace source to log the event to.</span></span>

- <span data-ttu-id="91461-191">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="91461-191">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="91461-192">Objekt, na kterém byla metoda volána.</span><span class="sxs-lookup"><span data-stu-id="91461-192">The object that the method was called on.</span></span>

- <span data-ttu-id="91461-193">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-193">`method` <xref:System.String></span></span>

  <span data-ttu-id="91461-194">Metoda, která je ukončována.</span><span class="sxs-lookup"><span data-stu-id="91461-194">The method that is being exited.</span></span>

- <span data-ttu-id="91461-195">`retObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="91461-195">`retObject` <xref:System.Object></span></span>

  <span data-ttu-id="91461-196">Hodnota, která je vrácena metodou.</span><span class="sxs-lookup"><span data-stu-id="91461-196">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-object-method"></a><span data-ttu-id="91461-197">Exit (TraceSource, řetězec, String, objekt) – metoda</span><span class="sxs-lookup"><span data-stu-id="91461-197">Exit(TraceSource, string, string, object) method</span></span>

<span data-ttu-id="91461-198">Protokoly se ukončí od funkce.</span><span class="sxs-lookup"><span data-stu-id="91461-198">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, object retObject)
```

### <a name="parameters"></a><span data-ttu-id="91461-199">Parametry</span><span class="sxs-lookup"><span data-stu-id="91461-199">Parameters</span></span>

- <span data-ttu-id="91461-200">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="91461-200">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="91461-201">Zdroj trasování pro zaprotokolování události do protokolu.</span><span class="sxs-lookup"><span data-stu-id="91461-201">The trace source to log the event to.</span></span>

- <span data-ttu-id="91461-202">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-202">`obj` <xref:System.String></span></span>

  <span data-ttu-id="91461-203">Objekt, na kterém byla metoda volána.</span><span class="sxs-lookup"><span data-stu-id="91461-203">The object that the method was called on.</span></span>

- <span data-ttu-id="91461-204">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-204">`method` <xref:System.String></span></span>

  <span data-ttu-id="91461-205">Metoda, která je ukončována.</span><span class="sxs-lookup"><span data-stu-id="91461-205">The method that is being exited.</span></span>

- <span data-ttu-id="91461-206">`retObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="91461-206">`retObject` <xref:System.Object></span></span>

  <span data-ttu-id="91461-207">Hodnota, která je vrácena metodou.</span><span class="sxs-lookup"><span data-stu-id="91461-207">The value that's being returned by the method.</span></span>

## <a name="exittracesource-object-string-string-method"></a><span data-ttu-id="91461-208">Exit (TraceSource, objekt, řetězec, String) – metoda</span><span class="sxs-lookup"><span data-stu-id="91461-208">Exit(TraceSource, object, string, string) method</span></span>

<span data-ttu-id="91461-209">Protokoly se ukončí od funkce.</span><span class="sxs-lookup"><span data-stu-id="91461-209">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, string retValue)
```

### <a name="parameters"></a><span data-ttu-id="91461-210">Parametry</span><span class="sxs-lookup"><span data-stu-id="91461-210">Parameters</span></span>

- <span data-ttu-id="91461-211">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="91461-211">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="91461-212">Zdroj trasování pro zaprotokolování události do protokolu.</span><span class="sxs-lookup"><span data-stu-id="91461-212">The trace source to log the event to.</span></span>

- <span data-ttu-id="91461-213">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="91461-213">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="91461-214">Objekt, na kterém byla metoda volána.</span><span class="sxs-lookup"><span data-stu-id="91461-214">The object that the method was called on.</span></span>

- <span data-ttu-id="91461-215">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-215">`method` <xref:System.String></span></span>

  <span data-ttu-id="91461-216">Metoda, která je ukončována.</span><span class="sxs-lookup"><span data-stu-id="91461-216">The method that is being exited.</span></span>

- <span data-ttu-id="91461-217">`retValue` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-217">`retValue` <xref:System.String></span></span>

  <span data-ttu-id="91461-218">Hodnota, která je vrácena metodou.</span><span class="sxs-lookup"><span data-stu-id="91461-218">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-string-method"></a><span data-ttu-id="91461-219">Exit (TraceSource; metoda; String; String; String)</span><span class="sxs-lookup"><span data-stu-id="91461-219">Exit(TraceSource, string, string, string) method</span></span>

<span data-ttu-id="91461-220">Protokoly se ukončí od funkce.</span><span class="sxs-lookup"><span data-stu-id="91461-220">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, string retValue)
```

### <a name="parameters"></a><span data-ttu-id="91461-221">Parametry</span><span class="sxs-lookup"><span data-stu-id="91461-221">Parameters</span></span>

- <span data-ttu-id="91461-222">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="91461-222">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="91461-223">Zdroj trasování pro zaprotokolování události do protokolu.</span><span class="sxs-lookup"><span data-stu-id="91461-223">The trace source to log the event to.</span></span>

- <span data-ttu-id="91461-224">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-224">`obj` <xref:System.String></span></span>

  <span data-ttu-id="91461-225">Objekt, na kterém byla metoda volána.</span><span class="sxs-lookup"><span data-stu-id="91461-225">The object that the method was called on.</span></span>

- <span data-ttu-id="91461-226">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-226">`method` <xref:System.String></span></span>

  <span data-ttu-id="91461-227">Metoda, která je ukončována.</span><span class="sxs-lookup"><span data-stu-id="91461-227">The method that is being exited.</span></span>

- <span data-ttu-id="91461-228">`retValue` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-228">`retValue` <xref:System.String></span></span>

  <span data-ttu-id="91461-229">Hodnota, která je vrácena metodou.</span><span class="sxs-lookup"><span data-stu-id="91461-229">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-method"></a><span data-ttu-id="91461-230">Exit (TraceSource, String, String) – metoda</span><span class="sxs-lookup"><span data-stu-id="91461-230">Exit(TraceSource, string, string) method</span></span>

<span data-ttu-id="91461-231">Protokoly se ukončí od funkce.</span><span class="sxs-lookup"><span data-stu-id="91461-231">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a><span data-ttu-id="91461-232">Parametry</span><span class="sxs-lookup"><span data-stu-id="91461-232">Parameters</span></span>

- <span data-ttu-id="91461-233">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="91461-233">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="91461-234">Zdroj trasování pro zaprotokolování události do protokolu.</span><span class="sxs-lookup"><span data-stu-id="91461-234">The trace source to log the event to.</span></span>

- <span data-ttu-id="91461-235">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-235">`method` <xref:System.String></span></span>

  <span data-ttu-id="91461-236">Metoda, která je ukončována.</span><span class="sxs-lookup"><span data-stu-id="91461-236">The method that is being exited.</span></span>

- <span data-ttu-id="91461-237">`parameters` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-237">`parameters` <xref:System.String></span></span>

  <span data-ttu-id="91461-238">Parametry, které byly předány metodě, která je ukončována.</span><span class="sxs-lookup"><span data-stu-id="91461-238">The parameters that were passed to the method that's being exited.</span></span>

## <a name="exittracesource-string-method"></a><span data-ttu-id="91461-239">Exit (TraceSourcete, String) – metoda</span><span class="sxs-lookup"><span data-stu-id="91461-239">Exit(TraceSource, string) method</span></span>

<span data-ttu-id="91461-240">Protokoly se ukončí od funkce.</span><span class="sxs-lookup"><span data-stu-id="91461-240">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string msg)
```

### <a name="parameters"></a><span data-ttu-id="91461-241">Parametry</span><span class="sxs-lookup"><span data-stu-id="91461-241">Parameters</span></span>

- <span data-ttu-id="91461-242">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="91461-242">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="91461-243">Zdroj trasování pro zaprotokolování události do protokolu.</span><span class="sxs-lookup"><span data-stu-id="91461-243">The trace source to log the event to.</span></span>

- <span data-ttu-id="91461-244">`msg` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="91461-244">`msg` <xref:System.String></span></span>

  <span data-ttu-id="91461-245">Zpráva ukončení pro přihlášení ke zdroji trasování.</span><span class="sxs-lookup"><span data-stu-id="91461-245">The exit message to log to the trace source.</span></span>

## <a name="http-property"></a><span data-ttu-id="91461-246">Vlastnost http</span><span class="sxs-lookup"><span data-stu-id="91461-246">Http property</span></span>

<span data-ttu-id="91461-247">Získá zdroj trasování pro System .NET. http.</span><span class="sxs-lookup"><span data-stu-id="91461-247">Gets the trace source for "System.Net.Http".</span></span>

```csharp
internal static TraceSource Http { get; }
```

### <a name="property-value"></a><span data-ttu-id="91461-248">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="91461-248">Property value</span></span>

<xref:System.Diagnostics.TraceSource>\
<span data-ttu-id="91461-249">Zdroj trasování pro System .NET. http nebo v `null` případě, že protokolování není povoleno.</span><span class="sxs-lookup"><span data-stu-id="91461-249">The trace source for "System.Net.Http", or `null` if logging is not enabled.</span></span>

## <a name="on-property"></a><span data-ttu-id="91461-250">Vlastnost on</span><span class="sxs-lookup"><span data-stu-id="91461-250">On property</span></span>

<span data-ttu-id="91461-251">Získá hodnotu, která označuje, zda je povoleno protokolování.</span><span class="sxs-lookup"><span data-stu-id="91461-251">Gets a value that indicates whether logging is enabled.</span></span>

```csharp
internal static bool On { get; }
```

### <a name="property-value"></a><span data-ttu-id="91461-252">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="91461-252">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="91461-253">`true`Pokud je povoleno protokolování; v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="91461-253">`true` if logging is enabled; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="91461-254">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91461-254">Requirements</span></span>

<span data-ttu-id="91461-255">**Obor názvů:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="91461-255">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="91461-256">**Sestavení:** Systém (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="91461-256">**Assembly:** System (in System.dll)</span></span>
