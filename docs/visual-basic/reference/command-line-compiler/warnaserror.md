---
title: -warnaserror (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: 1b8bc004705be4113d875dd7909426e2d253112d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534979"
---
# <a name="-warnaserror-visual-basic"></a>-warnaserror (Visual Basic)
Způsobí, že kompilátor první výskyt upozornění považovat za chybu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|+ &#124; -|Volitelné. Ve výchozím nastavení `-warnaserror-` je v platnosti; upozornění nezabrání kompilátor vytváří výstupní soubor. `-warnaserror` Možnost, která je stejná jako `-warnaserror+`, způsobí upozornění budou považována za chyby.|  
|`numberList`|Volitelné. Čárkami oddělený seznam ID upozornění čísla, ke kterému `-warnaserror` možnost se vztahuje. Pokud není zadána žádná ID upozornění, `-warnaserror` možnost se vztahuje na všechna upozornění.|  
  
## <a name="remarks"></a>Poznámky  
 `-warnaserror` Možnost zpracuje všechna upozornění jako chyby. Všechny zprávy, které by obvykle hlášeny jako varování jsou hlášeny jako chyby. Kompilátor oznámí další výskyty stejného upozornění jako upozornění.  
  
 Ve výchozím nastavení `-warnaserror-` je v platnosti, což způsobí, že upozornění bude pouze informační. `-warnaserror` Možnost, která je stejná jako `-warnaserror+`, způsobí upozornění budou považována za chyby.  
  
 Pokud chcete pouze několik specifická upozornění budou považována za chyby, můžete zadat čárkou oddělený seznam čísel upozornění pro nakládání s chybami.  
  
> [!NOTE]
>  `-warnaserror` Možnost neřídí, jak se zobrazí upozornění. Použití [- nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) možnost zakázat upozornění.  
  
|Chcete-li nastavit warnaserror – považovat všechna upozornění jako chyby v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  Mají projekt vybraný v **Průzkumníka řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte na tlačítko **kompilaci** kartu.<br />3.  Ujistěte se, **zakázat všechna upozornění** zaškrtávací políčko je zaškrtnuté políčko.<br />4.  Zkontrolujte, **považovat všechna upozornění jako chyby** zaškrtávací políčko.|  
  
|Chcete-li nastavit warnaserror – považovat specifická upozornění jako chyby v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  Mají projekt vybraný v **Průzkumníka řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.<br />2.  Klikněte na tlačítko **kompilaci** kartu.<br />3.  Ujistěte se, **zakázat všechna upozornění** zaškrtávací políčko je zaškrtnuté políčko.<br />4.  Ujistěte se, **považovat všechna upozornění jako chyby** zaškrtávací políčko je zaškrtnuté políčko.<br />5.  Vyberte **chyba** z **oznámení** sloupce sousedícího s upozornění, která mají být považována za chybu.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a instruuje kompilátor, aby zobrazuje chybu pro první výskyt každé varování, které nalezne.  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a pouze upozornění pro nepoužívané místní proměnné (42024) považuje za chybu.  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a>Viz také:
- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)
