---
title: -platform
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: a6226b73d5d5d4d48a71afe39e8a546019d4c0bc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352346"
---
# <a name="-platform-visual-basic"></a>– Platforma (Visual Basic)
Určuje, která verze platformy modulu CLR (Common Language Runtime) může spustit výstupní soubor.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termín|Definice|  
|---|---|  
|`x86`|Zkompiluje sestavení tak, aby bylo spuštěno pomocí 32 CLR kompatibilního s platformou x86.|  
|`x64`|Zkompiluje sestavení tak, aby bylo spuštěno pomocí 64 CLR na počítači, který podporuje instrukční sady AMD64 nebo EM64T.|  
|`Itanium`|Zkompiluje sestavení tak, aby bylo spuštěno pomocí 64 CLR v počítači s procesorem Itanium.|  
|`arm`|Zkompiluje sestavení, které se má spustit na počítači s procesorem ARM (Advanced RISC Machine).|  
|`anycpu`|Zkompiluje sestavení pro spuštění na libovolné platformě. Aplikace bude spuštěna jako 32ová aplikace v 32 verzích systému Windows a jako aplikace 64 64 v systému Windows v 16bitovém verzích. Tento příznak je výchozí hodnota.|  
|`anycpu32bitpreferred`|Zkompiluje sestavení pro spuštění na libovolné platformě. Aplikace bude spuštěna jako 32ová aplikace v 32 i v 64 bitových verzí systému Windows. Tento příznak je platný jenom pro spustitelné soubory (. EXE) a vyžaduje .NET Framework 4,5.|  
  
## <a name="remarks"></a>Poznámky  
 Pomocí možnosti `-platform` určete typ procesoru, který je cílem výstupního souboru.  
  
 Obecně platí, .NET Framework sestavení zapsaných v Visual Basic budou spuštěna stejně bez ohledu na platformu. Existují však některé případy, které se chovají odlišně na různých platformách. Tyto běžné případy:  
  
- Struktury, které obsahují členy, které mění velikost v závislosti na platformě, jako je například libovolný typ ukazatele.  
  
- Aritmetický ukazatel, který obsahuje konstantní velikosti.  
  
- Nesprávné vyvolání platformy nebo deklarace COM, které používají `Integer` pro popisovače místo <xref:System.IntPtr>.  
  
- Přetypování <xref:System.IntPtr> do `Integer`.  
  
- Použití volání platformy nebo zprostředkovatele komunikace s objekty COM s komponentami, které neexistují na všech platformách.  
  
 Pokud víte, že jste provedli předpoklady týkající se architektury, na které je váš kód spuštěný, možnost **-platformou** tyto problémy sníží. Určen  
  
- Pokud se rozhodnete cílit na 64 platformu a aplikace je spuštěná na 32 počítači, chybová zpráva je mnohem starší a cílená na problém je větší než chyba, ke které dojde bez použití tohoto přepínače.  
  
- Pokud u možnosti nastavíte příznak `x86` a aplikace se následně spustí na 64ém počítači, aplikace se spustí v subsystému WOW namísto nativního spuštění.  
  
 V 64 operačním systému Windows:  
  
- Sestavení kompilována s `-platform:x86` budou spouštěna v 32 CLR spuštěném v modulu WOW64.  
  
- Spustitelné soubory kompilovány s `-platform:anycpu` budou spouštěny v 64 CLR.  
  
- Knihovna DLL kompilována s `-platform:anycpu` bude spuštěna ve stejném modulu CLR jako proces, do kterého byla načtena.  
  
- Spustitelné soubory, které jsou kompilovány s `-platform:anycpu32bitpreferred`, budou spouštěny v 32 CLR.  
  
 Další informace o vývoji aplikace pro spuštění v 64 verze systému Windows naleznete v tématu [64-bitové aplikace](../../../framework/64-bit-apps.md).  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a>Nastavení platformy v integrovaném vývojovém prostředí sady Visual Studio  
  
1. V **Průzkumník řešení**zvolte projekt, otevřete nabídku **projekt** a klikněte na tlačítko **vlastnosti**.  
  
2. Na kartě **kompilovat** zaškrtněte nebo zrušte zaškrtnutí políčka **preferovat 32** , nebo v seznamu **cílový procesor** zvolte hodnotu.  
  
     Další informace naleznete v tématu [Kompilovat stránku, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít možnost kompilátoru `-platform`.  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [-Target (Visual Basic)](target.md)
- [Visual Basic Kompilátor příkazového řádku](index.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
