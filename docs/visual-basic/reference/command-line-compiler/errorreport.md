---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d093b8ce4413a375e79eec239be37e83ac674d05
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929940"
---
# <a name="-errorreport"></a>-errorreport

Určuje, jak by měl kompilátor jazyka Visual Basic ohlásit interní chyby kompilátoru.

## <a name="syntax"></a>Syntaxe

```
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a>Poznámky

Tato možnost poskytuje pohodlný způsob, jak sestavu jazyce Visual Basic vnitřní chyba kompilátoru (ICE) týmu Visual Basic v Microsoftu. Ve výchozím nastavení kompilátor odesílá žádné informace o společnosti Microsoft. Ale pokud narazíte na chybu kompilátoru, tato možnost umožňuje nahlásit chyby do Microsoftu. Tyto informace vám pomohou určit příčinu odborníky z Microsoftu a může zvýšit následující verzi jazyka Visual Basic.

Uživatele umožňuje odeslat sestavy závisí na počítače a uživatelských oprávnění zásad.

Následující tabulka shrnuje vliv `-errorreport` možnost.

|Možnost|Chování|
|---|---|
|`prompt`|Pokud dojde k chybě vnitřní kompilátor, dialogové okno se zobrazí tak, aby se zobrazí přesně ta data, která shromažďují kompilátor. Můžete určit, jestli nejsou k dispozici žádné citlivé informace v chybové zprávě a rozhodnutí na tom, zda chcete odesílat společnosti Microsoft. Pokud se rozhodnete odeslat a povolit nastavení zásad počítače a uživatele, kompilátor odesílá data do Microsoftu.|
|`queue`|Zařadí do fronty zprávy o chybách. Při přihlašování s použitím oprávnění správce, můžete nahlásit všechny chyby od posledního byly zaznamenány v (nezobrazí se výzva k odeslání zprávy o chybách více než jednou za tři dny). Toto je výchozí chování při `-errorreport` možnost není zadána.|
|`send`|Pokud dojde k chybě vnitřního kompilátoru a nastavení zásad počítače a uživatele nepovoluje, kompilátor odesílá data do Microsoftu.<br /><br /> Možnost `-errorreport:send` pokusí automaticky odesílat informace o chybách společnosti Microsoft, pokud vytváření sestav je povoleno podle [zasílání zpráv o chybách Windows](/windows/desktop/wer/windows-error-reporting) nastavení systému. |
|`none`|Pokud dojde k chybě vnitřní kompilátor, nebude shromážděné nebo odeslané společnosti Microsoft.|

Kompilátor odešle data, která zahrnuje zásobníku v době výskytu chyby, který obvykle obsahuje určitý zdrojový kód. Pokud `-errorreport` se používá s [- bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) možnost, celý zdrojový soubor je odeslaný.

Tato možnost je vhodné použít v [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) možnost, protože umožňuje technikům Microsoftu informace snadno chybu reprodukovat.

> [!NOTE]
> `-errorreport` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.

## <a name="example"></a>Příklad

Následující kód se pokusí zkompilovat `T2.vb`, a pokud kompilátor narazí vnitřní chyba kompilátoru, vyzve vás k odeslání zprávy o chybách společnosti Microsoft.

```
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a>Viz také:

- [Kompilátor příkazového řádku jazyka Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
