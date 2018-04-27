---
title: -errorreport
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5dc321f7f927d68a9f270076640cbc6d31d2f6d5
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="-errorreport"></a>-errorreport
Určuje, jak by měla Visual Basic – kompilátor zprávy o chybách interní kompilátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a>Poznámky  
 Tuto možnost nabízí pohodlný způsob, jak sestavy chybu interní kompilátoru jazyka Visual Basic (LED) týmu Visual Basic v Microsoftu. Ve výchozím nastavení kompilátoru odešle žádné informace společnosti Microsoft. Ale pokud dojde k chybě vnitřní kompilátoru, tato možnost umožňuje společnosti Microsoft zprávu o chybě. Tyto informace vám pomohou určit příčinu pracovníci společnosti Microsoft a může pomoct zlepšit další verzi jazyka Visual Basic.  
  
 Schopnost uživatele odesílat zprávy závisí na oprávnění zásad počítače a uživatele.  
  
 Následující tabulka shrnuje účinku `-errorreport` možnost.  
  
|Možnost|Chování|  
|---|---|  
|`prompt`|Pokud dojde k chybě vnitřní kompilátoru, dialogové okno se zobrazí tak, aby můžete zobrazit přesný data, která shromažďují kompilátoru. Můžete zjistit, jestli neexistuje žádné citlivé informace v chybové zprávě a provedení rozhodnutí na tom, zda je k odeslání společnosti Microsoft. Pokud se rozhodnete odeslat, a nastavení zásad počítače a uživatele, aby ji, kompilátor odešle data do Microsoftu.|  
|`queue`|Fronty zprávy o chybách. Když se přihlásíte pomocí oprávnění správce, můžete sestavu případných selhání od posledního byly přihlášení (nezobrazí se výzva k odeslání zpráv o selhání více než jednou za tři dní). Toto je výchozí chování při `-errorreport` není určena možnost.|  
|`send`|Pokud dojde k chybě vnitřní kompilátoru a nastavení zásad počítače a uživatele, aby ji, kompilátor odešle data do Microsoftu.<br /><br /> Možnost `-errorreport:send` pokusí automaticky odesílat informace o chybách společnosti Microsoft. Tuto možnost, závisí na registru. Další informace o nastavení na odpovídající hodnoty v registru najdete v tématu [jak zapnout automatické hlášení chyb v příkazového řádku nástroje sady Visual Studio 2008](http://go.microsoft.com/fwlink/?LinkID=184695).|  
|`none`|Pokud dojde k chybě vnitřní kompilátoru, nebudou shromažďovány nebo odesílány do společnosti Microsoft.|  
  
 Kompilátor odešle data, která zahrnuje zásobníku v době chyby, která obvykle zahrnuje některé zdrojového kódu. Pokud `-errorreport` se používá s [- bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) možnost, pak je odeslán celý zdrojový soubor.  
  
 Tato možnost je nejvhodnější pro [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) možnost, protože umožňuje snadno tomu chybu reprodukovat pracovníci společnosti Microsoft na informace.  
  
> [!NOTE]
>  `-errorreport` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód pokusí zkompilovat `T2.vb`, a pokud kompilátor dojde k chybě vnitřní kompilátoru, budete vyzváni k odeslání zprávy o chybách společnosti Microsoft.  
  
```  
vbc -errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
