---
description: -errorreport (možnosti kompilátoru C#)
title: -errorreport (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: 5b3143f4da81ac693626778263c277e3a484c45e
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125719"
---
# <a name="-errorreport-c-compiler-options"></a>-errorreport (možnosti kompilátoru C#)
Tato možnost nabízí pohodlný způsob, jak ohlásit vnitřní chybu kompilátoru v jazyce C# společnosti Microsoft.

> [!NOTE]
> V systémech Windows Vista a Windows Server 2008 nastavení zasílání zpráv o chybách, která uděláte pro Visual Studio, nepřepisují nastavení vytvořená prostřednictvím služby Zasílání zpráv o chybách systému Windows (WER). Nastavení funkce WER vždycky mají přednost před nastavením zasílání zpráv o chybách sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```console
-errorreport:{ none | prompt | queue | send }
```

## <a name="arguments"></a>Argumenty
 **žádný**  
 Zprávy o vnitřních chybách kompilátoru nebudou shromažďovány ani odesílány společnosti Microsoft.

 **Zobrazit výzvu** Vyzve vás k odeslání sestavy, když dojde k vnitřní chybě kompilátoru. při kompilaci aplikace ve vývojovém prostředí se **zobrazí dotaz** na výchozí hodnotu.

 **fronta** Zařadí do fronty zprávu o chybách. Když se přihlásíte s přihlašovacími údaji správce, můžete nahlásit všechny chyby od posledního přihlášení. Nebudete vyzváni k odeslání zpráv o selhání více než jednou za tři dny. při kompilaci aplikace na příkazovém řádku je **fronta** výchozí.

 **Odeslat** Automaticky odesílá zprávy o vnitřních chybách kompilátoru společnosti Microsoft. Pokud chcete povolit tuto možnost, musíte nejdřív souhlasit se zásadou pro shromažďování dat Microsoftu. Při prvním zadání **– errorreport: Send** v počítači, zpráva kompilátoru vás bude odkazovat na web, který obsahuje zásadu shromažďování dat společnosti Microsoft.

## <a name="remarks"></a>Poznámky
 Vnitřní chyba kompilátoru (ICE) má za následek, že kompilátor nemůže zpracovat soubor zdrojového kódu. Když dojde k ICE, kompilátor nevytvoří výstupní soubor nebo žádnou užitečnou diagnostiku, kterou můžete použít k opravě kódu.

 Pokud jste v předchozích verzích obdrželi ICE, doporučujeme kontaktovat oddělení služeb technické podpory společnosti Microsoft, aby nahlásila problém. Pomocí **-errorreport**můžete poskytnout informace o Ice týmu Visual C#. Vaše zprávy o chybách mohou pomoci vylepšit budoucí verze kompilátoru.

 Schopnost uživatele odesílat sestavy závisí na oprávněních pro počítače a uživatele.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete stránku **vlastností** projektu. Další informace naleznete v tématu [Stránka sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).

2. Klikněte na stránku vlastností **Build (sestavit** ).

3. Klikněte na tlačítko **Upřesnit** .

4. Upravte vlastnost **interního zasílání zpráv o chybách kompilátoru** .

 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A> .

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
