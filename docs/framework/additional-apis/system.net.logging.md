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
# <a name="logging-class"></a>Logging – třída

Poskytuje funkce protokolování trasování.

```csharp
internal class Logging
```

> [!WARNING]
> Tato třída je interní a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.

## <a name="associate-method"></a>Přidružte metodu

Protokoluje informace, ke kterým jsou přidruženy dva objekty.

```csharp
internal static void Associate(TraceSource traceSource, object objA, object objB)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Zdroj trasování pro zaprotokolování události do protokolu.

- `objA` <xref:System.Object>

  Objekt, ke kterému se má přidružit `objB` .

- `objB` <xref:System.Object>

  Objekt, ke kterému se má přidružit `objA` .

## <a name="entertracesource-object-string-string-method"></a>ENTER (TraceSource, Object, String, String) – metoda

Zapíše vstup do metody.

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, string param)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Zdroj trasování pro zaprotokolování události do protokolu.

- `obj` <xref:System.Object>

  Objekt, na kterém byla metoda volána.

- `method` <xref:System.String>

  Metoda, která je zadávána.

- `param` <xref:System.String>

  Parametry, které byly předány metodě.

## <a name="entertracesource-object-string-object-method"></a>ENTER (TraceSource; Object; String; objekt) – metoda

Zapíše vstup do metody.

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, object paramObject)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Zdroj trasování pro zaprotokolování události do protokolu.

- `obj` <xref:System.Object>

  Objekt, na kterém byla metoda volána.

- `method` <xref:System.String>

  Metoda, která je zadávána.

- `paramObject` <xref:System.Object>

  Parametry, které byly předány metodě.

## <a name="entertracesource-string-string-string-method"></a>ENTER (TraceSource, String, String, String) – metoda

Zapíše vstup do metody.

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, string param)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Zdroj trasování pro zaprotokolování události do protokolu.

- `obj` <xref:System.String>

  Objekt, na kterém byla metoda volána.

- `method` <xref:System.String>

  Metoda, která je zadávána.

- `param` <xref:System.String>

  Parametry, které byly předány metodě.

## <a name="entertracesource-string-string-object-method"></a>ENTER (TraceSource, String, String, objekt) – metoda

Zapíše vstup do metody.

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, object paramObject)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Zdroj trasování pro zaprotokolování události do protokolu.

- `obj` <xref:System.String>

  Objekt, na kterém byla metoda volána.

- `method` <xref:System.String>

  Metoda, která je zadávána.

- `paramObject` <xref:System.Object>

  Parametry, které byly předány metodě.

## <a name="entertracesource-string-string-method"></a>ENTER (TraceSource, String, String) – metoda

Zapíše vstup do metody.

```csharp
internal static void Enter(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Zdroj trasování pro zaprotokolování události do protokolu.

- `method` <xref:System.String>

  Metoda, která je zadávána.

- `parameters` <xref:System.String>

  Parametry, které byly předány metodě.

## <a name="entertracesource-string-method"></a>Enter – Metoda (TraceSource, String)

Zapíše vstup do metody.

```csharp
internal static void Enter(TraceSource traceSource, string msg)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Zdroj trasování pro zaprotokolování události do protokolu.

- `msg` <xref:System.String>

  Úvodní zpráva, která se má přihlásit ke zdroji trasování.

## <a name="exception-method"></a>Exception – metoda

Zaznamená výjimku a obnoví odsazení.

```csharp
internal static void Exception(TraceSource traceSource, object obj, string method, Exception e)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Zdroj trasování pro zaprotokolování události do protokolu.

- `obj` <xref:System.Object>

  Objekt, na kterém byla volána metoda, která vyvolala výjimku.

- `method` <xref:System.String>

  Metoda, která vyvolala výjimku.

- `e` <xref:System.Exception>

  Výjimka, která byla vyvolána.

## <a name="exittracesource-object-string-object-method"></a>Exit (TraceSource, objekt, String, objekt) – metoda

Protokoly se ukončí od funkce.

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, object retObject)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Zdroj trasování pro zaprotokolování události do protokolu.

- `obj` <xref:System.Object>

  Objekt, na kterém byla metoda volána.

- `method` <xref:System.String>

  Metoda, která je ukončována.

- `retObject` <xref:System.Object>

  Hodnota, která je vrácena metodou.

## <a name="exittracesource-string-string-object-method"></a>Exit (TraceSource, řetězec, String, objekt) – metoda

Protokoly se ukončí od funkce.

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, object retObject)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Zdroj trasování pro zaprotokolování události do protokolu.

- `obj` <xref:System.String>

  Objekt, na kterém byla metoda volána.

- `method` <xref:System.String>

  Metoda, která je ukončována.

- `retObject` <xref:System.Object>

  Hodnota, která je vrácena metodou.

## <a name="exittracesource-object-string-string-method"></a>Exit (TraceSource, objekt, řetězec, String) – metoda

Protokoly se ukončí od funkce.

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, string retValue)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Zdroj trasování pro zaprotokolování události do protokolu.

- `obj` <xref:System.Object>

  Objekt, na kterém byla metoda volána.

- `method` <xref:System.String>

  Metoda, která je ukončována.

- `retValue` <xref:System.String>

  Hodnota, která je vrácena metodou.

## <a name="exittracesource-string-string-string-method"></a>Exit (TraceSource; metoda; String; String; String)

Protokoly se ukončí od funkce.

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, string retValue)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Zdroj trasování pro zaprotokolování události do protokolu.

- `obj` <xref:System.String>

  Objekt, na kterém byla metoda volána.

- `method` <xref:System.String>

  Metoda, která je ukončována.

- `retValue` <xref:System.String>

  Hodnota, která je vrácena metodou.

## <a name="exittracesource-string-string-method"></a>Exit (TraceSource, String, String) – metoda

Protokoly se ukončí od funkce.

```csharp
internal static void Exit(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Zdroj trasování pro zaprotokolování události do protokolu.

- `method` <xref:System.String>

  Metoda, která je ukončována.

- `parameters` <xref:System.String>

  Parametry, které byly předány metodě, která je ukončována.

## <a name="exittracesource-string-method"></a>Exit (TraceSourcete, String) – metoda

Protokoly se ukončí od funkce.

```csharp
internal static void Exit(TraceSource traceSource, string msg)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Zdroj trasování pro zaprotokolování události do protokolu.

- `msg` <xref:System.String>

  Zpráva ukončení pro přihlášení ke zdroji trasování.

## <a name="http-property"></a>Vlastnost http

Získá zdroj trasování pro System .NET. http.

```csharp
internal static TraceSource Http { get; }
```

### <a name="property-value"></a>Hodnota vlastnosti

<xref:System.Diagnostics.TraceSource>\
Zdroj trasování pro System .NET. http nebo v `null` případě, že protokolování není povoleno.

## <a name="on-property"></a>Vlastnost on

Získá hodnotu, která označuje, zda je povoleno protokolování.

```csharp
internal static bool On { get; }
```

### <a name="property-value"></a>Hodnota vlastnosti

<xref:System.Boolean>\
`true`Pokud je povoleno protokolování; v opačném případě `false` .

## <a name="requirements"></a>Požadavky

**Obor názvů:**<xref:System.Net>

**Sestavení:** Systém (v System.dll)
