---
title: -subsystemversion (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22eb8aa1cd86dba4a1a65edf31a3b18df7085a33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654447"
---
# <a name="-subsystemversion-visual-basic"></a>-subsystemversion (Visual Basic)
Určuje minimální verze subsystému, ve kterém můžete spustit vygenerovaný spustitelný soubor, a určení verze systému Windows, ve kterém můžete spustit spustitelný soubor. Nejčastěji tato možnost zajistí, že spustitelný soubor můžete využít funkce konkrétní zabezpečení, které nejsou k dispozici se staršími verzemi Windows.  
  
> [!NOTE]
>  Pokud chcete zadat subsystém sám sebe, použijte [-cíl](../../../csharp/language-reference/compiler-options/target-compiler-option.md) – možnost kompilátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
-subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a>Parametry  
 `major.minor`  
 Minimální požadovaná verze subsystému, jak je vyjádřen v s tečkami pro hlavní verze a podverze. Například můžete zadat, že aplikace nelze spustit na operační systém, který je starší než Windows 7 Pokud nastavíte hodnotu tuto možnost na 6.01, podle popisu v tabulce dál v tomto tématu. Je potřeba zadat hodnoty pro `major` a `minor` jako celá čísla.  
  
 Program je zaměřen úvodní `minor` verze se nezmění na verzi, ale provést koncové nuly. Například 6.1 a 6.01 odkazovat na stejnou verzi, ale 6.10 odkazuje na jinou verzi. Doporučujeme, abyste vyjádření na podverzi jako dvě číslice k zamezení nejasnostem.  
  
## <a name="remarks"></a>Poznámky  
 V následující tabulce jsou uvedeny běžné subsystému verzích systému Windows.  
  
|Verze systému Windows|Verze subsystému|  
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
  
-   Výchozí hodnota je 6.02, pokud je nastavená žádné – možnost kompilátoru v následujícím seznamu:  
  
    -   [-target:appcontainerexe](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [-target:winmdobj](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [-platform: arm](../../../visual-basic/reference/command-line-compiler/platform.md)  
  
-   Výchozí hodnota je 6.00, pokud používáte nástroje MSBuild, jste cílení [!INCLUDE[net_v45](~/includes/net-v45-md.md)], a jste nenastavili některé z možností kompilátoru, která jste zadali dříve v tomto seznamu.  
  
-   Výchozí hodnota je 4.00, pokud žádná z předchozích podmínek.  
  
## <a name="setting-this-option"></a>Nastavení této možnosti  
 Chcete-li nastavit **- subsystemversion** – možnost kompilátoru v sadě Visual Studio, musíte otevřít soubor .vbproj a zadejte hodnotu pro `SubsystemVersion` vlastnost v souboru XML MSBuild. Tuto možnost nelze nastavit v integrovaném vývojovém prostředí sady Visual Studio. Další informace najdete v tématu "Výchozí hodnoty" dříve v tomto tématu nebo [běžné vlastnosti projektu nástroje MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).  
  

  
## <a name="see-also"></a>Viz také  
[Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)

[Vlastnosti nástroje MSBuild](/visualstudio/msbuild/msbuild-properties)
