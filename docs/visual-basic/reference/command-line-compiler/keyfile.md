---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: b113c2b0311f1f108e36b7a81e60818fe1c2c3df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529070"
---
# <a name="-keyfile"></a>-keyfile
Určuje soubor, který obsahuje klíč nebo dvojici klíčů poskytnout sestavení silným názvem.  
  
## <a name="syntax"></a>Syntaxe  
  
``` 
-keyfile:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Povinný parametr. Soubor, který obsahuje klíč. Pokud název souboru obsahuje mezery, uzavřete název do uvozovek ("").  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor vloží veřejný klíč do manifestu sestavení a poté podepíše konečné sestavení soukromým klíčem. Chcete-li generovat soubor s klíčem, zadejte `sn -k file` na příkazovém řádku. Další informace najdete v tématu [Sn.exe (nástroj Strong Name)][Sn.exe (nástroj Strong Name)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 Pokud kompilujete s `-target:module`, je název souboru klíče uložené v modulu a součástí sestavení, které se vytvoří, když kompilujete sestavení s [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Můžete také předat údaje o šifrování pro kompilátor [- keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md). Použití [- delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) potřebujete částečně podepsaného sestavení.  
  
 Tuto možnost lze také nastavit jako vlastní atribut (<xref:System.Reflection.AssemblyKeyFileAttribute>) ve zdrojovém kódu pro jakýkoli modul jazyka Microsoft.  
  
 V případě obě `-keyfile` a [- keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) zadávají (pomocí možnosti příkazového řádku nebo pomocí vlastního atributu) ve stejné kompilaci, kompilátor se pokusí nejprve kontejneru klíčů. Pokud tato operace úspěšná, sestavení je podepsáno pomocí informací v kontejneru klíčů. Pokud kompilátor nenajde kontejneru klíčů, pokusí se použít soubor určený `-keyfile`. Pokud se toto povede, sestavení je podepsáno informacemi ze souboru klíčů a informace o klíči se instaluje v kontejneru klíčů (podobné `sn -i`) tak, aby při další kompilaci bude platný kontejner klíčů.  
  
 Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.  
  
 Zobrazit [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) Další informace o podepisování sestavení.  
  
> [!NOTE]
>  `-keyfile` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód se zkompiluje zdrojový soubor `Input.vb` a určuje soubor klíče.  
  
```console  
vbc -keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a>Viz také:
- [Sestavení a globální mezipaměť sestavení (GAC)](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)
- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [– referenční dokumentace (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
