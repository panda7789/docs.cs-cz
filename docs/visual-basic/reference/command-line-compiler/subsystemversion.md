---
title: -subsystemversion (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
ms.openlocfilehash: c9920869a660bc6144749cc7584275be4608a7c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228806"
---
# <a name="-subsystemversion-visual-basic"></a>-subsystemversion (Visual Basic)
Určuje minimální verzi subsystému, na kterém poběží vygenerovaný spustitelný soubor, a tím určení verze Windows, na kterém můžete spustit spustitelný soubor. Nejčastěji tato možnost zajišťuje, že spustitelného souboru, který můžete využít konkrétní bezpečnostní funkce, které nejsou k dispozici ve starších verzích Windows.  
  
> [!NOTE]
>  K určení subsystému, sama, použijte [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) – možnost kompilátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
-subsystemversion:major.minor  
```  
  
## <a name="parameters"></a>Parametry  
 `major.minor`  
 Minimální požadovaná verze subsystému, jak je vyjádřen v zápisu s tečkou pro hlavní verze a podverze. Například můžete určit, že aplikaci nelze spustit v operačním systému, který je starší než Windows 7. Pokud nastavíte na hodnotu této možnosti 6.01, podle popisu v tabulce dále v tomto tématu. Je nutné zadat hodnoty pro `major` a `minor` jako celá čísla.  
  
 Program je zaměřen nejlepší `minor` verze se nezmění na verzi, ale proveďte koncové nuly. Například 6.1 a 6.01 odkazovat na stejnou verzi, ale 6.10 odkazuje na jinou verzi. Doporučujeme, abyste jako dvě číslice, aby nedocházelo k záměně vyjádření podverze.  
  
## <a name="remarks"></a>Poznámky  
 Následující tabulka uvádí nejběžnější verze subsystému Windows.  
  
|Verze Windows|Verze subsystému|  
|---------------------|-----------------------|  
|Windows 2000|5.00|  
|Windows XP|5.01|  
|Windows Server 2003|5.02|  
|Windows Vista|6.00|  
|Windows 7|6.01|  
|Windows Server 2008|6.01|  
|[!INCLUDE[win8](~/includes/win8-md.md)]|6.02|  
  
## <a name="default-values"></a>Výchozí hodnoty  
 Výchozí hodnota **- subsystemversion** – možnost kompilátoru závisí na podmínkách v následujícím seznamu:  
  
-   Výchozí hodnota je 6.02, je-li nastavit všechny možnosti kompilátoru v následujícím seznamu:  
  
    -   [-target:appcontainerexe](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [-target:winmdobj](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [-platform: arm](../../../visual-basic/reference/command-line-compiler/platform.md)  
  
-   Výchozí hodnota je 6.00, pokud používáte MSBuild, které cílíte [!INCLUDE[net_v45](~/includes/net-v45-md.md)], a jste nenastavili žádné možnosti kompilátoru, která jste zadali dříve v tomto seznamu.  
  
-   Výchozí hodnota je 4.00, pokud žádná z předchozích podmínek není splněna.  
  
## <a name="setting-this-option"></a>Nastavení této možnosti  
 Chcete-li nastavit **- subsystemversion** – možnost kompilátoru v sadě Visual Studio, otevřete soubor .vbproj a zadejte hodnotu pro `SubsystemVersion` vlastnost v XML nástroje MSBuild. Tuto možnost nelze nastavit v integrovaném vývojovém prostředí sady Visual Studio. Další informace najdete v tématu "Výchozí hodnoty" výše v tomto tématu nebo [obecné vlastnosti projektu nástroje MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).  

## <a name="see-also"></a>Viz také:

- [Kompilátor příkazového řádku jazyka Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)

- [Vlastnosti nástroje MSBuild](/visualstudio/msbuild/msbuild-properties)
