---
title: /bugreport
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0c36cdcaf8d2db0b08e262d6ba8ff2bb774fb233
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="bugreport"></a>/bugreport
Vytvoří soubor, který můžete použít, když soubor sestavy chyb.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/bugreport:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`file`|Požadováno. Název souboru, který bude obsahovat sestavy chyb. Uzavřete název souboru v uvozovkách ("") Pokud název obsahuje mezeru.|  
  
## <a name="remarks"></a>Poznámky  
 Následující informace, které jsou přidány do `file`:  
  
-   Kopírování všech souborů zdrojového kódu v kompilace.  
  
-   Seznam možností kompilátoru použita při kompilaci.  
  
-   Informace o verzi o kompilátoru, modul common language runtime a operačního systému.  
  
-   Výstup kompilátoru, pokud existuje.  
  
-   Popis problému, pro který se zobrazí výzva.  
  
-   Popis jak domníváte, že problém je třeba stanovit, pro který se zobrazí výzva.  
  
 Protože je součástí kopii všechny soubory zdrojového kódu `file`, možná budete chtít reprodukovat (možného) kód do nejkratší programu.  
  
> [!IMPORTANT]
>  `/bugreport` Možnost vytvoří soubor, který obsahuje potenciálně citlivé informace. To zahrnuje aktuální čas, verze kompilátoru [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] verze, verze operačního systému, uživatelské jméno, argumenty příkazového řádku, se kterými kompilátor bylo spuštěno, všechny zdrojového kódu a binárního formátu všech odkazovaná sestavení. Tato možnost je přístupná zadáním možnosti příkazového řádku v souboru Web.config pro kompilaci na straně serveru [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplikace. Chcete-li tomu zabránit, upravte souboru Machine.config. Chcete-li zakázat uživatelům v kompilaci na serveru.  
  
 Pokud tato možnost se používá s `/errorreport:prompt`, `/errorreport:queue`, nebo `/errorreport:send`, a aplikace, dojde k chybě vnitřní kompilátoru, informace v `file` je odeslány společnosti Microsoft Corporation. Tyto informace vám pomohou určit příčinu chyby pracovníci společnosti Microsoft a může pomoct zlepšit další verzi [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]. Ve výchozím nastavení je odeslány žádné informace společnosti Microsoft. Ale při kompilaci aplikace pomocí `/errorreport:queue`, který je ve výchozím nastavení povolené, aplikace shromažďuje jeho zprávy o chybách. Pak když se na správce přihlásí, zobrazí se chyba systému místní okno, které umožňuje správcům předávat je společnosti Microsoft sestavy všechny chyby, které došlo od přihlášení.  
  
> [!NOTE]
>  `/bugreport` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici, pouze při sestavování z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje `T2.vb` a vloží všechny informace o vytváření sestav chyb v souboru `Problem.txt`.  
  
```  
vbc /bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [/errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [trustLevel Element pro securityPolicy (schéma nastavení ASP.NET)](http://msdn.microsoft.com/library/729ab04c-03da-4ee5-86b1-be9d08a09369)
