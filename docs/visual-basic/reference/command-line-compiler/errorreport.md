---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
ms.openlocfilehash: b6a1c8fce17e3e5a54366c2ff4dff4e6aa668f56
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408657"
---
# <a name="-errorreport"></a>-errorreport

Určuje, jak by měl kompilátor Visual Basic hlásit vnitřní chyby kompilátoru.

## <a name="syntax"></a>Syntaxe

```console
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a>Poznámky

Tato možnost poskytuje pohodlný způsob, jak ohlásit Visual Basic vnitřní chybu kompilátoru (ICE) týmu Visual Basic v Microsoftu. Ve výchozím nastavení kompilátor neodesílá společnosti Microsoft žádné informace. Pokud ale dojde k vnitřní chybě kompilátoru, tato možnost vám umožní ohlásit chybu společnosti Microsoft. Tyto informace pomohou technikům Microsoftu identifikovat příčinu a mohou vám pomoci vylepšit další vydání Visual Basic.

Schopnost uživatele odesílat sestavy závisí na oprávněních pro počítače a uživatele.

Následující tabulka shrnuje efekt `-errorreport` Možnosti.

|Možnost|Chování|
|---|---|
|`prompt`|Pokud dojde k vnitřní chybě kompilátoru, zobrazí se dialogové okno, abyste mohli zobrazit přesná data, která kompilátor shromáždil. Můžete určit, jestli se v hlášení o chybách nacházejí nějaké citlivé informace, a rozhodnout se, jestli se má poslat Microsoftu. Pokud se rozhodnete ho odeslat a nastavení zásad počítače a uživatele ho povolí, kompilátor pošle data společnosti Microsoft.|
|`queue`|Zařadí do fronty zprávu o chybách. Když se přihlásíte s oprávněními správce, můžete nahlásit všechny chyby od posledního přihlášení (nebudete vyzváni k odeslání zpráv o selhání více než jednou za tři dny). Toto je výchozí chování, pokud není `-errorreport` zadána možnost.|
|`send`|Pokud dojde k vnitřní chybě kompilátoru a nastavení zásad počítače a uživatele je povolí, kompilátor odesílá data společnosti Microsoft.<br /><br /> Možnost se do `-errorreport:send` Microsoftu pokusí automaticky odeslat informace o chybě, pokud je generování sestav povolené nastavením systému [zasílání zpráv o chybách systému Windows](/windows/desktop/wer/windows-error-reporting) . |
|`none`|Dojde-li k vnitřní chybě kompilátoru, nebude shromažďována ani odeslána společnosti Microsoft.|

Kompilátor odesílá data, která zahrnují zásobník v době chyby, což obvykle zahrnuje nějaký zdrojový kód. Pokud `-errorreport` se používá s možností [-bugreport –](bugreport.md) , pak se pošle celý zdrojový soubor.

Tato možnost se nejlépe používá s možností [-bugreport –](bugreport.md) , protože umožňuje vývojářům Microsoftu snadněji reprodukování chyby.

> [!NOTE]
> Tato `-errorreport` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.

## <a name="example"></a>Příklad

Následující kód se pokusí kompilovat `T2.vb` , a pokud kompilátor narazí na vnitřní chybu kompilátoru, zobrazí výzvu k odeslání zprávy o chybách společnosti Microsoft.

```console
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
- [-bugreport](bugreport.md)
