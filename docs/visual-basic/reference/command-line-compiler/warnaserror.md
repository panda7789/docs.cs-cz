---
title: -warnaserror
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: 94a8b43a891df9837925869e17fac4536a995264
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414269"
---
# <a name="-warnaserror-visual-basic"></a>-warnaserror – (Visual Basic)
Způsobí, že kompilátor bude zacházet s prvním výskytem upozornění jako s chybou.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Pojem|Definice|  
|---|---|  
|+ &#124; –|Nepovinný parametr. Ve výchozím nastavení `-warnaserror-` platí; upozornění nebrání kompilátoru v vytváření výstupního souboru. `-warnaserror`Možnost, která je stejná jako `-warnaserror+` , způsobí, že upozornění budou považována za chyby.|  
|`numberList`|Nepovinný parametr. Seznam čísel ID upozornění oddělených čárkami, na které se `-warnaserror` možnost vztahuje. Pokud není zadané žádné ID upozornění, bude `-warnaserror` možnost platit pro všechna upozornění.|  
  
## <a name="remarks"></a>Poznámky  
 `-warnaserror`Možnost zpracovává všechna upozornění jako chyby. Všechny zprávy, které by byly obvykle hlášeny jako upozornění, jsou místo toho hlášeny jako chyby. Kompilátor ohlásí následné výskyty stejného upozornění jako upozornění.  
  
 Ve výchozím nastavení `-warnaserror-` je to v platnosti, což způsobí, že upozornění budou pouze informativní. `-warnaserror`Možnost, která je stejná jako `-warnaserror+` , způsobí, že upozornění budou považována za chyby.  
  
 Pokud chcete, aby se jako chyby považovala jenom některá konkrétní upozornění, můžete zadat čárkami oddělený seznam čísel upozornění, která se budou považovat za chyby.  
  
> [!NOTE]
> `-warnaserror`Možnost neurčuje, jak se zobrazují upozornění. Pro vypnutí upozornění použijte možnost [-](nowarn.md) upozornění.  
  
|Nastavení-warnaserror –, aby považovala všechna upozornění jako chyby v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1. v **Průzkumník řešení**mít vybraný projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**. <br />2. klikněte na kartu **kompilovat** .<br />3. Ujistěte se, že není zaškrtnuté políčko **Zakázat všechna upozornění** .<br />4. zaškrtněte políčko **považovat všechna upozornění za chyby** .|  
  
|Nastavení-warnaserror – pro zacházení s konkrétními upozorněními jako s chybami v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1. v **Průzkumník řešení**mít vybraný projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**.<br />2. klikněte na kartu **kompilovat** .<br />3. Ujistěte se, že není zaškrtnuté políčko **Zakázat všechna upozornění** .<br />4. Ujistěte se, že není zaškrtnuté políčko **považovat všechna upozornění jako chyby** .<br />5. Vyberte **chybu** ze sloupce **oznámení** vedle upozornění, které by mělo být považováno za chybu.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a nasměruje kompilátor, aby zobrazil chybu pro první výskyt každého upozornění, které najde.  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a považuje pouze upozornění na nepoužívané místní proměnné (42024) jako chybu.  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
- [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)
