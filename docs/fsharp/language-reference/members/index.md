---
title: Členové
description: Přečtěte si o členech F# objektů v programovacím jazyce.
ms.date: 05/16/2016
ms.openlocfilehash: 2e85d014cd1e9b7997638cb210fed5705c217719
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425074"
---
# <a name="members"></a>Členové

Tato část popisuje členy typů F# objektů.

## <a name="remarks"></a>Poznámky

*Členové* jsou funkce, které jsou součástí definice typu a jsou deklarovány pomocí klíčového slova `member`. F#členy podporují typy objektů, jako jsou záznamy, třídy, rozlišené sjednocení, rozhraní a struktury. Další informace naleznete v tématu [záznamy](../records.md), [třídy](../classes.md), [rozlišené sjednocení](../discriminated-Unions.md), [rozhraní](../interfaces.md)a [struktury](../structures.md).

Členové obvykle tvoří veřejné rozhraní pro typ, což je důvod, proč jsou veřejné, pokud není uvedeno jinak. Členy mohou být také deklarovány jako soukromé nebo interní. Další informace najdete v tématu [Access Control](../access-Control.md). Signatury pro typy lze také použít k vystavení nebo vystavení určitých členů typu. Další informace najdete v tématu [signatury](../signature-files.md).

Soukromá pole a `do` vazby, které jsou používány pouze s třídami, nejsou skutečnými členy, protože nejsou součástí veřejného rozhraní typu a nejsou deklarovány s klíčovým slovem `member`, ale jsou popsány také v této části.

## <a name="related-topics"></a>Související témata

|Téma|Popis|
|-----|-----------|
|[`let` vazby v třídách](let-bindings-in-classes.md)|Popisuje definici privátních polí a funkcí ve třídách.|
|[`do` vazby v třídách](do-bindings-in-classes.md)|Popisuje specifikace inicializačního kódu objektu.|
|[Vlastnosti](properties.md)|Popisuje členy vlastnosti v třídách a dalších typech.|
|[Indexované vlastnosti](indexed-properties.md)|Popisuje vlastnosti typu pole v třídách a dalších typech.|
|[Metody](methods.md)|Popisuje funkce, které jsou členy typu.|
|[Konstruktory](constructors.md)|Popisuje speciální funkce, které inicializují objekty typu.|
|[Přetížení operátoru](../operator-overloading.md)|Popisuje definici přizpůsobených operátorů pro typy.|
|[Události](events.md)|Popisuje definici událostí a podporu zpracování událostí v F#nástroji.|
|[Explicitní pole: Klíčové slovo `val`](explicit-fields-the-val-keyword.md)|Popisuje definici neinicializovaných polí v typu.|
