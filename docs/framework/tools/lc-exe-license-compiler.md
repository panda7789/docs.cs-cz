---
title: Lc.exe (kompilátor licencí)
ms.date: 03/30/2017
helpviewer_keywords:
- Lc.exe
- .licx file
- License Compiler
- control licenses [Windows Forms]
- compiling licenses file
- license file
- .licenses file
- Windows Forms, control licenses
- licensed controls [Windows Forms]
ms.assetid: 2de803b8-495e-4982-b209-19a72aba0460
ms.openlocfilehash: 464514a241cc35fc821049ba0c29bec108d88253
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180400"
---
# <a name="lcexe-license-compiler"></a>Lc.exe (kompilátor licencí)
License Compiler čte textové soubory, které obsahují licenční informace a vytváří binární soubor, který může být integrován jako prostředek do spustitelného souboru modulu CLR (Common Language Runtime).  
  
 Textový soubor .licx se automaticky vygeneruje nebo aktualizuje prostřednictvím Návrháře formulářů Windows pokaždé, když je do formuláře přidán licencovaný ovládací prvek. Jako část kompilace bude systém projektu transformovat textový soubor .licx na binární prostředek .licenses, který podporuje licencování ovládacích prvků .NET. Binární prostředek bude poté vložen do výstupu projektu.  
  
 Křížová kompilace mezi 32 bity a 64 bity není podporována, jestliže při sestavování projektu použijete License Compiler. Důvodem je, že License Compiler musí načíst sestavení, přičemž načítání 64bitových sestavení z 32bitové aplikace není povoleno a naopak. V tomto případě použijte License Compiler z příkazového řádku k ruční kompilaci licence a zadejte odpovídající architekturu.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console
      lc /target:  
targetPE /complist:filename [-outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/complist:** *název souboru*|Určuje název souboru, který obsahuje seznam licencovaných součástí, jež chcete zahrnout do souboru .licenses. Jednotlivé komponenty se odkazují pomocí úplného názvu, vždy pouze jedna komponenta na řádek.<br /><br /> Uživatelé příkazového řádku mohou určit samostatný soubor pro každý formulář v projektu. Lc.exe akceptuje více vstupních souborů a vytváří jeden soubor .licenses.|  
|**/h**[**elp**]|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/i:** *modul*|Určuje moduly, které obsahují součásti uvedené v souboru **/complist.** Chcete-li zadat více než jeden modul, použijte více příznaků **/i.**|  
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|**/outdir:** *cesta*|Určuje adresář, do kterého má být umístěn výstupní soubor .licenses.|  
|**/cíl:** *targetPE*|Určuje spustitelný soubor, pro který je generován soubor .licenses.|  
|**/v**|Určuje režim podrobného vypisování; zobrazuje informace o průběhu kompilace.|  
|**@***soubor*|Určuje soubor odpovědi (.rsp).|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="example"></a>Příklad  
  
1. Pokud používáte licencovaný `MyCompany.Samples.LicControl1` ovládací prvek `Samples.DLL` obsažený v `HostApp.exe`aplikaci `HostAppLic.txt` s názvem *,* můžete vytvořit následující.  
  
    ```text
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2. Vytvořte soubor .licenses s názvem `HostApp.exe.licenses` pomocí následujícího příkazu.  
  
    ```console  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3. Sestavení `HostApp.exe` včetně souboru .licenses jako prostředku. Pokud vytváříte aplikace C#, měli byste k sestavení aplikace použít následující příkaz.  
  
    ```console
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 Následující příkaz se `myApp.licenses` zkompiluje ze `hostapplic.txt`seznamů licencovaných součástí určených v položkách , `hostapplic2.txt` a `hostapplic3.txt`. Argument `modulesList` určuje moduly, které obsahují licencované součásti.  
  
```console  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a>Příklad souboru odpovědi  
 Následující výpis ukazuje příklad souboru `response.rsp`odpovědí . Další informace o souborech odpovědí naleznete v [tématu Response Files](/visualstudio/msbuild/msbuild-response-files).  
  
```text  
/target:hostapp.exe  
/complist:hostapplic.txt
/i:WFCPrj.dll
/outdir:"C:\My Folder"  
```  
  
 Soubor používá následující `response.rsp` příkazový řádek.  
  
```console  
lc @response.rsp  
```  
  
## <a name="see-also"></a>Viz také

- [Nástroje](index.md)
- [Al.exe (linker sestavení)](al-exe-assembly-linker.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
