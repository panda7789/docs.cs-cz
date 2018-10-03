---
title: -subsystemversion (možnosti kompilátoru C#)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: ff4cd196edc1ec04f8abcecfa1a7a4e99e32dd56
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48025443"
---
# <a name="-subsystemversion-c-compiler-options"></a>-subsystemversion (možnosti kompilátoru C#)
Určuje minimální verzi subsystému, na kterém poběží vygenerovaný spustitelný soubor, a tím určení verze Windows, na kterém můžete spustit spustitelný soubor. Nejčastěji tato možnost zajišťuje, že spustitelného souboru, který můžete využít konkrétní bezpečnostní funkce, které nejsou k dispozici ve starších verzích Windows.  
  
> [!NOTE]
>  K určení subsystému, sama, použijte [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) – možnost kompilátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a>Parametry  
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
  
    -   [-target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
  
    -   [-target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
  
    -   [-platform: arm](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)  
  
-   Výchozí hodnota je 6.00, pokud používáte MSBuild, které cílíte [!INCLUDE[net_v45](~/includes/net-v45-md.md)], a jste nenastavili žádné možnosti kompilátoru, která jste zadali dříve v tomto seznamu.  
  
-   Výchozí hodnota je 4.00, pokud žádná z předchozích podmínek není splněna.  
  
## <a name="setting-this-option"></a>Nastavení této možnosti  
 Chcete-li nastavit **- subsystemversion** – možnost kompilátoru v sadě Visual Studio, otevřete soubor .csproj a zadejte hodnotu pro `SubsystemVersion` vlastnost v XML nástroje MSBuild. Tuto možnost nelze nastavit v integrovaném vývojovém prostředí sady Visual Studio. Další informace najdete v tématu "Výchozí hodnoty" výše v tomto tématu nebo [obecné vlastnosti projektu nástroje MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).  
  
## <a name="see-also"></a>Viz také  

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
