---
title: Implicitní převod z '<typename1>' na '<typename2>' při kopírování hodnoty 'ByRef' parametru '<parametername> zpět na odpovídající argument
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: 4d0f9aac795f683cf58210ea38b3783e451ccfc3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402859"
---
# <a name="implicit-conversion-from-typename1-to-typename2-in-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument"></a>Implicitní převod z '\<typename1>' na '\<typename2>' při kopírování hodnoty 'ByRef' parametru '\<parametername> zpět na odpovídající argument
Procedura je volána s argumentem [ByRef](../modifiers/byref.md) jiného typu než odpovídajícím parametrem.  
  
 Pokud předáte argument `ByRef` , Visual Basic někdy zkopíruje hodnotu argumentu do místní proměnné v proceduře namísto předání odkazu. V takovém případě, když se procedura vrátí, Visual Basic nutné zkopírovat hodnotu lokální proměnné zpátky do argumentu v volajícím kódu.  
  
 Pokud `ByRef` je do procedury zkopírována hodnota argumentu a argument a parametr je stejného typu, není nutný žádný převod. Pokud se však typy liší, Visual Basic nutné převést v obou směrech. Vzhledem k tomu, že nemůžete použít `CType` ani žádná jiná klíčová slova převodu pro argument procedury nebo parametr, je takový převod vždy implicitní.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC41999  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud je to možné, použijte jako parametr procedury volající argument stejného typu, takže Visual Basic nemusí provádět žádné konverze.  
  
- Pokud potřebujete zavolat proceduru s typem argumentu odlišným od typu parametru, ale nemusíte vracet hodnotu do argumentu volání, definujte parametr jako [ByVal](../modifiers/byval.md) namísto `ByRef` .  
  
## <a name="see-also"></a>Viz také

- [Procedury](../../programming-guide/language-features/procedures/index.md)
- [Parametry a argumenty procedury](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Předávání argumentů podle hodnoty a reference](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [Implicitní a explicitní převody](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
