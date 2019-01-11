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
ms.openlocfilehash: 9f6daa696ecd7b91c6d53edaa447f2d64bca0fd7
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221203"
---
# <a name="lcexe-license-compiler"></a>Lc.exe (kompilátor licencí)
License Compiler čte textové soubory, které obsahují licenční informace a vytváří binární soubor, který může být integrován jako prostředek do spustitelného souboru modulu CLR (Common Language Runtime).  
  
 Textový soubor .licx se automaticky vygeneruje nebo aktualizuje prostřednictvím Návrháře formulářů Windows pokaždé, když je do formuláře přidán licencovaný ovládací prvek. Jako část kompilace bude systém projektu transformovat textový soubor .licx na binární prostředek .licenses, který podporuje licencování ovládacích prvků .NET. Binární prostředek bude poté vložen do výstupu projektu.  
  
 Křížová kompilace mezi 32 bity a 64 bity není podporována, jestliže při sestavování projektu použijete License Compiler. Důvodem je, že License Compiler musí načíst sestavení, přičemž načítání 64bitových sestavení z 32bitové aplikace není povoleno a naopak. V tomto případě použijte License Compiler z příkazového řádku k ruční kompilaci licence a zadejte odpovídající architekturu.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7). Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
      lc /target:  
      targetPE /complist:filename [/outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/complist:** *název souboru*|Určuje název souboru, který obsahuje seznam licencovaných součástí, jež chcete zahrnout do souboru .licenses. Jednotlivé komponenty se odkazují pomocí úplného názvu, vždy pouze jedna komponenta na řádek.<br /><br /> Uživatelé příkazového řádku mohou určit samostatný soubor pro každý formulář v projektu. Lc.exe akceptuje více vstupních souborů a vytváří jeden soubor .licenses.|  
|**/h**[**elp**]|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**i:** *modulu*|Určuje moduly obsahující uvedené v součásti **/complist** souboru. Pokud chcete zadat více než jeden modul, použijte více **/i** příznaky.|  
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|**/OutDir:** *cesta*|Určuje adresář, do kterého má být umístěn výstupní soubor .licenses.|  
|**/ target:** *targetPE*|Určuje spustitelný soubor, pro který je generován soubor .licenses.|  
|**/v**|Určuje režim podrobného vypisování; zobrazuje informace o průběhu kompilace.|  
|**@** *Soubor*|Určuje soubor odpovědí (.rsp).|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="example"></a>Příklad  
  
1.  Pokud používáte licencovaného ovládacího prvku `MyCompany.Samples.LicControl1` součástí `Samples.DLL` v aplikaci s názvem `HostApp.exe` *,* můžete vytvořit `HostAppLic.txt` , který obsahuje následující.  
  
    ```  
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2.  Vytvořte soubor .licenses s názvem `HostApp.exe.licenses` pomocí následujícího příkazu.  
  
    ```  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3.  Sestavení `HostApp.exe` včetně souboru .licenses jako prostředku. Pokud vytváříte aplikace C#, měli byste k sestavení aplikace použít následující příkaz.  
  
    ```  
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 Následující příkaz kompiluje `myApp.licenses` ze seznamu licencovaných součástí určených `hostapplic.txt`, `hostapplic2.txt` a `hostapplic3.txt`. `modulesList` Argument určuje moduly obsahující licencované komponenty.  
  
```  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a>Příklad souboru odpovědí  
 Následující výpis ukazuje příklad souboru odpovědí, `response.rsp`. Další informace o souborech odpovědí najdete v tématu [soubory odpovědí](/visualstudio/msbuild/msbuild-response-files).  
  
```  
/target:hostapp.exe  
/complist:hostapplic.txt   
/i:WFCPrj.dll   
/outdir:"C:\My Folder"  
```  
  
 Následující příkazový řádek používá `response.rsp` souboru.  
  
```  
lc @response.rsp  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Al.exe (linker sestavení)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
