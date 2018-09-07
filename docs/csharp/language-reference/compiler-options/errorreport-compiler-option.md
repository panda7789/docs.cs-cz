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
ms.openlocfilehash: dcbb9467da87a82147176bb0feb00383aff2c77f
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44069495"
---
# <a name="-errorreport-c-compiler-options"></a>-errorreport (možnosti kompilátoru C#)
Tato možnost poskytuje pohodlný způsob, jak nahlásit chybu kompilátoru jazyka C# společnosti Microsoft.  
  
> [!NOTE]
>  Ve Windows Vista a Windows Server 2008 nastavení generování sestav chyb, které jste udělali ve Visual Studio přepsat nastavení provedená prostřednictvím Windows Chyba vytváření sestav (zasílání). Nastavení zasílání vždy přednost před nastavením hlášení chyb sady Visual Studio.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-errorreport:{ none | prompt | queue | send }  
```  
  
## <a name="arguments"></a>Arguments  
 **None**  
 Sestavy o vnitřních chybách kompilátoru nebudou shromážděné nebo odeslané společnosti Microsoft.  
  
 **prompt**  
 Zobrazí výzvu k odeslání hlášení, pokud obdržíte chybu kompilátoru. **řádek** výchozí nastavení je při kompilaci aplikace ve vývojovém prostředí.  
  
 **fronty**  
 Zařadí do fronty zprávy o chybách. Při přihlášení s přihlašovacími údaji správce, můžete nahlásit všechny chyby od posledního přihlášení. Nezobrazí výzva k odeslání zprávy o chybách více než jednou za tři dny. **fronty** výchozí nastavení je při kompilaci aplikace příkazového řádku.  
  
 **Odeslat**  
 Automaticky posílá do Microsoftu zprávy o vnitřních chybách kompilátoru. Chcete-li tuto možnost povolte, musíte nejdříve souhlasit s zásady shromažďování údajů společnosti Microsoft. Když se poprvé zadáte **- errorreport: Odeslat** na počítači, bude zpráva kompilátoru odkazovat na web, který obsahuje zásady sběru dat společnosti Microsoft.  
    
## <a name="remarks"></a>Poznámky  
 Vnitřní chyba kompilátoru (ICE) výsledky, když kompilátor nemůže zpracovat soubor zdrojového kódu. Pokud dojde k ICE, kompilátor nevytvoří výstupní soubor nebo užitečnou diagnostiku, která můžete použít jak kód opravit.  
  
 V předchozích verzích při přijetí ICE jste vyzkoušeli Kontaktujte Microsoft Product Support Services nahlásit problém. S použitím **- errorreport**, můžete zadat informace o ICE týmu Visual C#. Zprávy o chybách můžete zvýšit kompilátoru budoucích verzí.  
  
 Uživatele umožňuje odeslat sestavy závisí na oprávnění zásad počítače a uživatele.  
  
 Další informace o ladění chyb, naleznete v tématu [Popis zotavení po havárii. Nástroje Watson pro Windows (Drwtsn32.exe)](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete v projektu **vlastnosti** stránky. Další informace najdete v tématu [stránku sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Klikněte na tlačítko **sestavení** stránku vlastností.  
  
3.  Klikněte na tlačítko **Upřesnit** tlačítko.  
  
4.  Upravit **hlášení vnitřních chyb kompilátoru** vlastnost.  
  
 Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.  
  
## <a name="see-also"></a>Viz také  

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
