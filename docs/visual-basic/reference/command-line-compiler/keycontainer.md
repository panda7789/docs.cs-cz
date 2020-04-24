---
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
ms.openlocfilehash: be2ad1416e801398fb513593c7f3828e5488bfaf
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005527"
---
# <a name="-keycontainer"></a>-keycontainer
Určuje název kontejneru klíče pro dvojici klíčů, který poskytne sestavení silného názvu.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-keycontainer:container  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Označení|Definice|  
|---|---|  
|`container`|Povinná hodnota. Soubor kontejneru, který obsahuje klíč. Uzavřete název souboru do uvozovek (""), pokud název obsahuje mezeru.|  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor vytvoří součást, kterou může sdílet, vložením veřejného klíče do manifestu sestavení a podepsáním konečného sestavení pomocí privátního klíče. Chcete-li vygenerovat soubor klíče `sn -k file` , zadejte do příkazového řádku. `-i` Možnost nainstaluje dvojici klíčů do kontejneru. Další informace naleznete v tématu [sn. exe (Nástroj pro silný název)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 Pokud kompilujete s `-target:module`, název souboru klíče je uložen v modulu a začleněn do sestavení, které je vytvořeno při kompilaci sestavení pomocí [-addmodule –](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Tuto možnost lze také zadat jako vlastní atribut (<xref:System.Reflection.AssemblyKeyNameAttribute>) ve zdrojovém kódu pro libovolný modul jazyka MSIL (Microsoft Intermediate Language).  
  
 Můžete také předat informace o šifrování kompilátoru s parametrem [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md). Použijte [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) , pokud chcete použít částečně podepsané sestavení.  
  
 Další informace o podepsání sestavení naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) .  
  
> [!NOTE]
> Tato `-keycontainer` možnost není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje zdrojový soubor `Input.vb` a určí kontejner klíčů.  
  
```console  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a>Viz také

- [Sestavení v .NET](../../../standard/assembly/index.md)
- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
