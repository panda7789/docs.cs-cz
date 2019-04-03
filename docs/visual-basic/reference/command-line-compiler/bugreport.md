---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: e7b4ebc58b6fe9850b92ef945cb0d715e4369efe
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820904"
---
# <a name="-bugreport"></a>-bugreport
Vytvoří soubor, který vám pomůže při souboru hlášení o chybě.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`file`|Povinný parametr. Název souboru, který bude obsahovat vaše hlášení o chybě. Název souboru uzavřete do uvozovek ("") Pokud název obsahuje mezery.|  
  
## <a name="remarks"></a>Poznámky  
 Následující informace se přidají do `file`:  
  
-   Zkopírujte všechny soubory zdrojového kódu dané kompilace.  
  
-   Seznam možností kompilátoru použita při kompilaci.  
  
-   Informace o verzi kompilátoru, modul common language runtime a operačního systému.  
  
-   Výstup kompilátoru, pokud existuje.  
  
-   Popis problému, pro který se zobrazí výzva.  
  
-   Popis jak domníváte, že problém je třeba stanovit, pro který se zobrazí výzva.  
  
 Vzhledem k tomu, že kopie všech souborů zdrojového kódu je součástí `file`, možná budete chtít reprodukovat (podezřelý) kód v nejkratší možné program.  
  
> [!IMPORTANT]
>  `-bugreport` Možnost vytvoří soubor, který obsahuje potenciálně citlivé informace. Jedná se o aktuální čas, verze kompilátoru [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] verzi, verze operačního systému, uživatelské jméno, argumenty příkazového řádku, pomocí kterých kompilátor byla spuštěna, s veškerým zdrojovým kódem a binární forma všechny odkazované sestavení. Tuto možnost můžete přistupovat zadáním možnosti příkazového řádku v souboru Web.config pro kompilaci na straně serveru z [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplikace. Chcete-li tomu zabránit, upravte soubor Machine.config chcete zakázat uživatelům v kompilaci na serveru.  
  
 Pokud tato možnost se používá s `-errorreport:prompt`, `-errorreport:queue`, nebo `-errorreport:send`, a aplikace zaznamená chybu kompilátoru, informace v `file` odeslány společnosti Microsoft Corporation. Tyto informace vám pomohou určit příčinu chyby odborníky z Microsoftu a může zvýšit následující verzi jazyka Visual Basic. Ve výchozím nastavení žádné informace se neposílají do Microsoftu. Nicméně pokud kompilujete aplikace s použitím `-errorreport:queue`, který je ve výchozím nastavení povolené, aplikace shromáždí jeho zprávy o chybách. Potom při přihlášení správce počítače, Chyba při vytváření sestav systému zobrazí automaticky otevírané okno, které umožňuje správcům předávání do Microsoftu zprávy o všech chybách, ke které došlo od přihlášení.  
  
> [!NOTE]
>  `/bugreport` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici, pouze pokud kompilujete z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující příklad se zkompiluje `T2.vb` a umístí všechny informace pro hlášení chyb v souboru `Problem.txt`.  
  
```  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [-debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)
- [-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [trustLevel – Element pro securityPolicy (schéma nastavení technologie ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))
