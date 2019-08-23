---
title: -appconfig (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 7a7e8e61f65704a2e99385a1be320048d950324c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922524"
---
# <a name="-appconfig-c-compiler-options"></a>-appconfig (C# možnosti kompilátoru)
Možnost kompilátoru **-appconfig** umožňuje C# aplikaci určit umístění souboru konfigurace aplikace (App. config) sestavení pro modul CLR (Common Language Runtime) v době vytváření vazby sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Povinný parametr. Konfigurační soubor aplikace, který obsahuje nastavení vazby sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Jedno použití **-appconfig** je pokročilé scénáře, ve kterých sestavení musí odkazovat jak na verzi .NET Framework, tak na .NET Framework pro verzi Silverlight konkrétního referenčního sestavení ve stejnou dobu. Například Návrhář XAML napsaný v Windows Presentation Foundation (WPF) může být nutné odkazovat jak na Desktop WPF, tak na uživatelském rozhraní návrháře a na podmnožinu WPF, která je součástí programu Silverlight. Stejné sestavení návrháře má přístup k oběma sestavením. Ve výchozím nastavení samostatné odkazy způsobí chybu kompilátoru, protože vazba sestavení uvidí dvě sestavení jako ekvivalentní.  
  
 Možnost kompilátoru **-appconfig** umožňuje určit umístění souboru App. config, který zakáže výchozí chování pomocí `<supportPortability>` značky, jak je znázorněno v následujícím příkladu.  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 Kompilátor předá umístění souboru do logiky vytváření vazeb sestavení CLR.  
  
> [!NOTE]
> Pokud k sestavení aplikace používáte Microsoft Build Engine (MSBuild), můžete nastavit možnost kompilátoru **-appconfig** přidáním značky vlastnosti do souboru. csproj. Chcete-li použít soubor App. config, který je již nastaven v projektu, přidejte do `<UseAppConfigForCompiler>` souboru. csproj značku vlastnosti a nastavte jeho hodnotu na `true`. Chcete-li zadat jiný soubor App. config, přidejte značku `<AppConfigForCompiler>` vlastnosti a nastavte její hodnotu na umístění souboru.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje soubor App. config, který umožňuje, aby aplikace měla odkazy na implementaci .NET Framework a .NET Framework pro implementaci technologie Silverlight pro jakékoli .NET Framework sestavení, které existuje v obou implementacích. Možnost kompilátoru **-appconfig** určuje umístění tohoto souboru App. config.  
  
```xml  
<configuration>  
      <runtime>  
      <assemblyBinding>  
            <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
            <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
      </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [\<Značka supportPortability – element >](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [Možnosti kompilátoru jazyka C# (abecední pořadí)](./listed-alphabetically.md)
