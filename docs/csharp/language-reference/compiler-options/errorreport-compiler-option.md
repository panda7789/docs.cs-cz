---
title: -errorreport (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: 52b58aac5e82d4228dfda9c4d77c1d1c5de3e0cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253882"
---
# <a name="-errorreport-c-compiler-options"></a>-errorreport (Možnosti kompilátoru Jazyka C#)
Tato možnost poskytuje pohodlný způsob, jak nahlásit chybu interního kompilátoru jazyka C# společnosti Microsoft.

> [!NOTE]
> V systémech Windows Vista a Windows Server 2008 nastavení zasílání zpráv o chybách, která provedete pro aplikaci Visual Studio, nepřepíší nastavení provedená prostřednictvím systému Windows Error Reporting (WER). Nastavení WER má vždy přednost před nastavením zasílání zpráv o chybách sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```console
-errorreport:{ none | prompt | queue | send }
```

## <a name="arguments"></a>Argumenty
 **žádný**  
 Zprávy o interních chybách kompilátoru nebudou shromažďovány ani odesílány společnosti Microsoft.

 **výzva** Zobrazí výzvu k odeslání sestavy, když se zobrazí vnitřní chyba kompilátoru. **výzva** je výchozí při kompilaci aplikace ve vývojovém prostředí.

 **fronta** Zařadí zprávu o chybě do fronty. Při přihlášení pomocí pověření pro správu můžete hlásit všechny chyby od posledního přihlášení. Nebudete vyzváni k odesílání zpráv o selhání více než jednou za tři dny. **fronta** je výchozí při kompilaci aplikace na příkazovém řádku.

 **odeslat** Automaticky odesílá zprávy o interních chybách kompilátoru společnosti Microsoft. Chcete-li tuto možnost povolit, musíte nejprve souhlasit se zásadami shromažďování dat společnosti Microsoft. Při prvním zadání **-errorreport:send** v počítači vás zpráva kompilátoru přejde na web, který obsahuje zásady shromažďování dat společnosti Microsoft.

## <a name="remarks"></a>Poznámky
 Vnitřní chyba kompilátoru (ICE) je výsledkem, když kompilátor nemůže zpracovat soubor zdrojového kódu. Dojde-li ICE, kompilátor nevytváří výstupní soubor nebo užitečnou diagnostiku, kterou můžete použít k opravě kódu.

 V předchozích verzích, když jste obdrželi ICE, byli jste vyzváni, abyste se obrátili na služby odborné pomoci společnosti Microsoft a nahlásili problém. Pomocí **-errorreport**můžete poskytnout ice informace týmu Visual C#. Vaše zprávy o chybách mohou pomoci zlepšit budoucí verze kompilátoru.

 Možnost uživatele odesílat sestavy závisí na oprávněních zásad počítače a uživatele.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete stránku **Vlastnosti** projektu. Další informace naleznete v [tématu Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).

2. Klikněte na stránku vlastností **Sestavení.**

3. Klepněte na tlačítko **Upřesnit.**

4. Upravte vlastnost **Interní zasílání zpráv o chybách kompilátoru.**

 Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>kompilátoru programově, naleznete v tématu .

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
