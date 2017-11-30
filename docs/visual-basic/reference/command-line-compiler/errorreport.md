---
title: /errorreport
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0abe276aaacdeb175c3af7067dffa81448450e22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="errorreport"></a>/errorreport
Určuje, jak [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilátoru by měl zprávy o chybách interní kompilátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato možnost nabízí pohodlný způsob, jak sestavu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] vnitřní chyba kompilátoru (LED) k [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] týmu ve společnosti Microsoft. Ve výchozím nastavení kompilátoru odešle žádné informace společnosti Microsoft. Ale pokud dojde k chybě vnitřní kompilátoru, tato možnost umožňuje společnosti Microsoft zprávu o chybě. Tyto informace vám pomohou určit příčinu pracovníci společnosti Microsoft a může pomoct zlepšit další verzi [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
 Schopnost uživatele odesílat zprávy závisí na oprávnění zásad počítače a uživatele.  
  
 Následující tabulka shrnuje účinku `/errorreport` možnost.  
  
|Možnost|Chování|  
|---|---|  
|`prompt`|Pokud dojde k chybě vnitřní kompilátoru, dialogové okno se zobrazí tak, aby můžete zobrazit přesný data, která shromažďují kompilátoru. Můžete zjistit, jestli neexistuje žádné citlivé informace v chybové zprávě a provedení rozhodnutí na tom, zda je k odeslání společnosti Microsoft. Pokud se rozhodnete odeslat, a nastavení zásad počítače a uživatele, aby ji, kompilátor odešle data do Microsoftu.|  
|`queue`|Fronty zprávy o chybách. Když se přihlásíte pomocí oprávnění správce, můžete sestavu případných selhání od posledního byly přihlášení (nezobrazí se výzva k odeslání zpráv o selhání více než jednou za tři dní). Toto je výchozí chování při `/errorreport` není určena možnost.|  
|`send`|Pokud dojde k chybě vnitřní kompilátoru a nastavení zásad počítače a uživatele, aby ji, kompilátor odešle data do Microsoftu.<br /><br /> Možnost `/errorReport:send` pokusí automaticky odesílat informace o chybách společnosti Microsoft. Tuto možnost, závisí na registru. Další informace o nastavení na odpovídající hodnoty v registru najdete v tématu [jak zapnout automatické hlášení chyb v příkazového řádku nástroje sady Visual Studio 2008](http://go.microsoft.com/fwlink/?LinkID=184695).|  
|`none`|Pokud dojde k chybě vnitřní kompilátoru, nebudou shromažďovány nebo odesílány do společnosti Microsoft.|  
  
 Kompilátor odešle data, která zahrnuje zásobníku v době chyby, která obvykle zahrnuje některé zdrojového kódu. Pokud `/errorreport` se používá s [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) možnost, pak je odeslán celý zdrojový soubor.  
  
 Tato možnost je nejvhodnější pro [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) možnost, protože umožňuje snadno tomu chybu reprodukovat pracovníci společnosti Microsoft na informace.  
  
> [!NOTE]
>  `/errorreport` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód pokusí zkompilovat `T2.vb`, a pokud kompilátor dojde k chybě vnitřní kompilátoru, budete vyzváni k odeslání zprávy o chybách společnosti Microsoft.  
  
```  
vbc /errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [/ bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
