---
title: Členy (F#)
description: 'Další informace o objektu členy v programovací jazyk F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 6dcdb1d7fa061fb838d4aa8f7a2912fd168c3781
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562203"
---
# <a name="members"></a>Členové

Tato část popisuje členy typy objektů F #.


## <a name="remarks"></a>Poznámky
*Členové* jsou funkce, které jsou součástí definice typu a jsou deklarovány s `member` – klíčové slovo. Objekt typů F # například záznamy, třídy, rozlišované sjednocení, rozhraní, a struktury podporují členy. Další informace najdete v tématu [záznamy](../records.md), [třídy](../classes.md), [Rozlišované sjednocení](../discriminated-Unions.md), [rozhraní](../interfaces.md), a [struktury](../structures.md).

Členové obvykle tvoří veřejné rozhraní pro typ, který je důvod, proč jsou veřejné, pokud není uvedeno jinak. Členy lze deklarovat také soukromý nebo interní. Další informace najdete v tématu [řízení přístupu](../access-Control.md). Podpisy pro typy lze také vystavit nebo není odhalí určité členy typu. Další informace najdete v tématu [podpisy](../signatures.md).

Soukromé pole a `do` vazby, které se používají pouze s třídami, nejsou členy hodnotu true, protože nikdy jsou součástí veřejného rozhraní typu a nejsou deklarovat s `member` – klíčové slovo, ale jsou popsané v této části taky.


## <a name="related-topics"></a>Související témata


|Téma|Popis|
|-----|-----------|
|[`let` Vazby do ve třídách](let-bindings-in-classes.md)|Popisuje definice privátní pole a funkce ve třídách.|
|[`do` Vazby do ve třídách](do-bindings-in-classes.md)|Popisuje specifikace kód inicializace objektu.|
|[Vlastnosti](properties.md)|Popisuje vlastnost členy v třídami a ostatními typy.|
|[Indexované vlastnosti](indexed-properties.md)|Popisuje vlastnosti jako pole v třídami a ostatními typy.|
|[Metody](methods.md)|Popisuje funkce, které jsou členy typu.|
|[Konstruktory](constructors.md)|Popisuje speciální funkce, které inicializovat objekty typu.|
|[Přetížení operátoru](../operator-overloading.md)|Popisuje definice přizpůsobené operátory pro typy.|
|[Události](events.md)|Popisuje definice události a události zpracování podpory v jazyce F #.|
|[Explicitní pole: Klíčové slovo `val`](explicit-fields-the-val-keyword.md)|Popisuje definice Neinicializovaný pole v typu.|
