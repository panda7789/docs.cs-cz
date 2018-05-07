---
title: -errorreport (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: d7e001834d670e7c88488c6db887d1d8e671beef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-errorreport-c-compiler-options"></a>-errorreport (možnosti kompilátoru C#)
Tato možnost nabízí pohodlný způsob, jak chybu interní kompilátoru C# nahlásit společnosti Microsoft.  
  
> [!NOTE]
>  Chyba vytváření sestav nastavení, která učiníte v sadě Visual Studio v systému Windows Vista a Windows Server 2008, nepotlačí nastavení provedená prostřednictvím systému Windows (zasílání chyb). Nastavení WER vždy mají přednost před nastavením hlášení chyb sady Visual Studio.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-errorreport:{ none | prompt | queue | send }  
```  
  
## <a name="arguments"></a>Arguments  
 **None**  
 Zprávy o chybách interní kompilátoru nebudou shromažďovány nebo odesílány do společnosti Microsoft.  
  
 **prompt**  
 Dotaz, zda chcete poslat zprávu, když obdrží vnitřní chyby kompilátoru. **řádku** je výchozí hodnota při kompilaci aplikace ve vývojovém prostředí.  
  
 **Fronty**  
 Fronty zprávy o chybách. Při přihlášení s přihlašovacími údaji správce může hlásit případných selhání od posledního přihlášení. Nebudou vyzváni k odeslání zpráv o selhání více než jednou za tři dny. **fronty** při kompilaci aplikace na příkazovém řádku je výchozí hodnota.  
  
 **Odeslat**  
 Zprávy o chybách interní kompilátoru automaticky odesílá společnosti Microsoft. Chcete-li tuto možnost, musíte nejprve souhlasit s zásad shromažďování dat Microsoft. Při prvním zadáte **- errorreport: Odeslat** v počítači, bude zpráva kompilátoru odkáže na web, který obsahuje zásady shromažďování dat Microsoft.  
    
## <a name="remarks"></a>Poznámky  
 Vnitřní chyba kompilátoru (LED) nastává kompilátor nemůže zpracovat soubor zdrojového kódu. Když dojde LED, kompilátor nevytváří výstupní soubor nebo užitečnou diagnostiku, můžete použít k opravě kódu.  
  
 V předchozích verzích při přijetí LED, jste vyzváni ke kontaktování oddělení Microsoft Product Support Services nahlásit problém. Pomocí **- errorreport**, můžete zadat informace LED týmu Visual C#. Zprávy o chybách může pomoct zlepšit budoucí vydání kompilátoru.  
  
 Schopnost uživatele odesílat zprávy závisí na oprávnění zásad počítače a uživatele.  
  
 Další informace o ladění chyb naleznete v tématu [Popis zotavení po havárii. Watson pro systém Windows (Drwtsn32.exe)](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **vlastnosti** stránky. Další informace najdete v tématu [stránka sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Klikněte **sestavení** stránku vlastností.  
  
3.  Klikněte **Upřesnit** tlačítko.  
  
4.  Změnit **interní hlášení chyb kompilátoru** vlastnost.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
