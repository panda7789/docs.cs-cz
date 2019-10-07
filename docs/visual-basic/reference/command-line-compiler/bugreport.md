---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 46d726332806f7d1f6e80dd7df31867051276b45
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002347"
---
# <a name="-bugreport"></a>-bugreport
Vytvoří soubor, který můžete použít při zaznamenání zprávy o chybě.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`file`|Požadováno. Název souboru, který bude obsahovat zprávu o chybě. Uzavřete název souboru do uvozovek (""), pokud název obsahuje mezeru.|  
  
## <a name="remarks"></a>Poznámky  
 Do `file` jsou přidány následující informace:  
  
- Kopii všech souborů zdrojového kódu v kompilaci.  
  
- Seznam možností kompilátoru použitých v kompilaci.  
  
- Informace o verzi pro kompilátor, modul CLR (Common Language Runtime) a operační systém.  
  
- Výstup kompilátoru, pokud existuje.  
  
- Popis problému, pro který se zobrazí výzva.  
  
- Popis toho, jak si myslíte problém, by měl být vyřešen, pro který se zobrazí výzva.  
  
 Vzhledem k tomu, že kopie všech souborů zdrojového kódu je součástí `file`, možná budete chtít reprodukování vady kódu (podezřelé) v nejkratším možném programu.  
  
> [!IMPORTANT]
> Možnost `-bugreport` vytvoří soubor, který obsahuje potenciálně citlivé informace. Patří sem aktuální čas, verze kompilátoru, verze .NET Framework, verze operačního systému, uživatelské jméno, argumenty příkazového řádku, s nimiž byl kompilátor spuštěn, veškerý zdrojový kód a binární forma libovolného odkazovaného sestavení. Tato možnost je k dispozici při zadání možností příkazového řádku v souboru Web. config pro kompilaci ASP.NET aplikace na straně serveru. Chcete-li tomu zabránit, upravte soubor Machine. config tak, aby nedocházelo k tomu, aby uživatelé mohli kompilovat na serveru.  
  
 Pokud je tato možnost použita s `-errorreport:prompt`, `-errorreport:queue` nebo `-errorreport:send` a vaše aplikace narazí na vnitřní chybu kompilátoru, informace v `file` se odešlou společnosti Microsoft Corporation. Tyto informace pomohou technikům Microsoftu identifikovat příčinu chyby a mohou pomoci zlepšit další vydání Visual Basic. Ve výchozím nastavení se Microsoftu neodesílají žádné informace. Pokud však zkompilujete aplikaci pomocí `-errorreport:queue`, což je ve výchozím nastavení povoleno, aplikace shromáždí své zprávy o chybách. Až se správce počítače přihlásí, systém zasílání zpráv o chybách zobrazí automaticky otevírané okno, které správci umožní předávat společnosti Microsoft jakékoli zprávy o chybách, ke kterým došlo od přihlášení.  
  
> [!NOTE]
> Možnost `/bugreport` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje `T2.vb` a vloží všechny informace o hlášení chyb v souboru `Problem.txt`.  
  
```console  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)
- [-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Element trustLevel pro securityPolicy (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))
