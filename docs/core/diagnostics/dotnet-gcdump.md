---
title: dotnet – gcdump – .NET Core
description: Instalace a použití nástroje příkazového řádku dotnet-gcdump.
ms.date: 07/26/2020
ms.openlocfilehash: a7b19f4d7487677b975621e7267a17894dae2e3a
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656648"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a>Nástroj pro analýzu haldy (dotnet – gcdump)

**Tento článek se týká:** ✔️ .net Core 3,1 SDK a novějších verzí

## <a name="install-dotnet-gcdump"></a>Instalace dotnet – gcdump

Chcete-li nainstalovat nejnovější verzi `dotnet-gcdump` [balíčku NuGet](https://www.nuget.org/packages/dotnet-gcdump), použijte příkaz pro [instalaci nástroje dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install -g dotnet-gcdump
```

## <a name="synopsis"></a>Stručný obsah

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a>Popis

`dotnet-gcdump`Globální nástroj je způsob, jak shromažďovat výpisy GC (uvolňování paměti) pro živé procesy .NET. Používá technologii EventPipe, což je alternativa k ETW v systému Windows, která je jiná pro různé platformy. Výpisy paměti GC se vytvářejí aktivací GC v cílovém procesu, zapnutím zvláštních událostí a obnovením grafu kořenových adresářů objektů z datového proudu událostí. Tento proces umožňuje shromáždit výpisy paměti GC, pokud je proces spuštěný a s minimální režií. Tyto výpisy jsou užitečné pro několik scénářů:

- Porovnání počtu objektů v haldě v několika okamžicích v čase.
- Analyzují se kořeny objektů (zodpovězené otázky, jako je například "co stále obsahuje odkaz na tento typ?").
- Shromažďování obecných statistik o počtu objektů v haldě.

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a>Zobrazit výpis GC zachycený z dotnet-gcdump

V systému Windows `.gcdump` lze soubory zobrazit v [PerfView](https://github.com/microsoft/perfview) pro účely analýzy nebo v aplikaci Visual Studio. V současné době neexistuje žádný způsob, jak otevřít `.gcdump` na platformách jiných než Windows.

Můžete shromáždit vícenásobné `.gcdump` a otevřít je současně v aplikaci Visual Studio a získat tak prostředí pro porovnání.

## <a name="options"></a>Možnosti

- **`--version`**

  Zobrazuje verzi `dotnet-gcdump` nástroje.

- **`-h|--help`**

  Zobrazí pomocníka s příkazovým řádkem.

## `dotnet-gcdump collect`

Shromažďuje výpis GC z aktuálně spuštěného procesu.

### <a name="synopsis"></a>Stručný obsah

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a>Možnosti

- **`-h|--help`**

  Zobrazí pomocníka s příkazovým řádkem.

- **`-p|--process-id <pid>`**

  ID procesu, ze kterého se má shromáždit výpis paměti.

- **`-o|--output <gcdump-file-path>`**

  Cesta, kam se mají zapisovat výpisy paměti GC Výchozí hodnota je *. \\ RRRRMMDD \_ HHMMSS \_ \<pid> . gcdump*.

- **`-v|--verbose`**

  Výstup protokolu při shromažďování výpisu paměti GC.

- **`-t|--timeout <timeout>`**

  Zastavte shromažďování výpisu paměti, pokud trvá déle než tento počet sekund. Výchozí hodnota je 30.

- **`-n|--name <name>`**

  Název procesu, ze kterého se má shromáždit výpis paměti.

## `dotnet-gcdump ps`

Zobrazuje seznam procesů dotnet, pro které lze shromáždit výpisy paměti GC.

### <a name="synopsis"></a>Stručný obsah

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

Vygenerujte sestavu z dříve generovaného výpisu GC nebo ze spuštěného procesu a zapište do `stdout` .

### <a name="synopsis"></a>Stručný obsah

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a>Možnosti

- **`-h|--help`**

  Zobrazí pomocníka s příkazovým řádkem.

- **`-p|--process-id <pid>`**

  ID procesu, ze kterého se má shromáždit výpis paměti.

- **`-t|--report-type <HeapStat>`**

  Typ sestavy, která má být vygenerována. Dostupné možnosti: heapstat (výchozí).

## <a name="troubleshoot"></a>Řešení potíží

- V gcdump nejsou žádné informace o typu.

   Před rozhraním .NET Core 3,1 došlo k potížím s nesmazáním mezipaměti typů mezi gcdumps, pokud byly vyvolány pomocí EventPipe. Výsledkem jsou události potřebné k určení typu informací, které nejsou odesílány pro druhý a další gcdumps. Tento problém byl opravený v .NET Core 3,1-preview2.

- COM a statické typy nejsou ve výpisu GC.

   Před rozhraním .NET Core 3,1-preview2 došlo k problému, kdy se při vyvolání výpisu paměti GC prostřednictvím EventPipe neodeslaly statické a COM typy. Tento problém byl opraven v rozhraní .NET Core 3,1-preview2.
