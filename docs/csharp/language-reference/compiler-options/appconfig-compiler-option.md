---
title: -appconfig (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 7a7e8e61f65704a2e99385a1be320048d950324c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69922524"
---
# <a name="-appconfig-c-compiler-options"></a>-appconfig (Možnosti kompilátoru Jazyka C#)
Možnost kompilátoru **-appconfig** umožňuje aplikaci C# určit umístění souboru konfigurace aplikace sestavení (app.config) do souboru CLR (COMMON Language runtime) v době vazby sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Povinná hodnota. Konfigurační soubor aplikace, který obsahuje nastavení vazby sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Jedním z použití **-appconfig** je pokročilé scénáře, ve kterých sestavení musí odkazovat na verzi rozhraní .NET Framework a rozhraní .NET Framework pro verzi programu Silverlight konkrétního referenčního sestavení současně. Například návrhář XAML napsaný v systému Windows Presentation Foundation (WPF) může mít odkazovat jak wpf desktop, pro uživatelské rozhraní návrháře a podmnožinu WPF, který je součástí Programu Silverlight. Stejné sestavení návrháře má přístup k oběma sestavením. Ve výchozím nastavení samostatné odkazy způsobit chybu kompilátoru, protože vazba sestavení vidí dvě sestavení jako ekvivalentní.  
  
 Možnost kompilátoru **-appconfig** umožňuje určit umístění souboru app.config, který zakáže výchozí chování pomocí `<supportPortability>` značky, jak je znázorněno v následujícím příkladu.  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 Kompilátor předá umístění souboru clr je vázající logiku sestavení.  
  
> [!NOTE]
> Pokud k vytvoření aplikace používáte modul Microsoft Build Engine (MSBuild), můžete nastavit možnost kompilátoru **-appconfig** přidáním značky vlastnosti do souboru .csproj. Chcete-li použít soubor app.config, který je již `<UseAppConfigForCompiler>` v projektu nastaven, přidejte do `true`souboru .csproj značku vlastnosti a nastavte jeho hodnotu na . Chcete-li zadat jiný soubor app.config, přidejte značku `<AppConfigForCompiler>` vlastnosti a nastavte její hodnotu na umístění souboru.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje soubor app.config, který umožňuje aplikaci mít odkazy na implementaci rozhraní .NET Framework a rozhraní .NET Framework pro implementaci rozhraní Silverlight libovolného sestavení rozhraní .NET Framework, které existuje v obou implementacích. Možnost kompilátoru **-appconfig** určuje umístění tohoto souboru app.config.  
  
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
  
## <a name="see-also"></a>Viz také

- [\<supportPortability> Element](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [Možnosti kompilátoru C# (abecední pořadí)](./listed-alphabetically.md)
