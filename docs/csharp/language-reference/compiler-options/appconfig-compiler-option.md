---
description: -appconfig (možnosti kompilátoru C#)
title: -appconfig (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 287d41105199057add1dad78d480b083adb745b2
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126109"
---
# <a name="-appconfig-c-compiler-options"></a>-appconfig (možnosti kompilátoru C#)
Možnost kompilátoru **-appconfig** umožňuje aplikaci v jazyce C# určit umístění souboru konfigurace aplikace (app.config) sestavení pro modul CLR (Common Language Runtime) v době vytváření vazby sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Povinná hodnota. Konfigurační soubor aplikace, který obsahuje nastavení vazby sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Jedno použití **-appconfig** je pokročilé scénáře, ve kterých sestavení musí odkazovat jak na verzi .NET Framework, tak na .NET Framework pro verzi Silverlight konkrétního referenčního sestavení ve stejnou dobu. Například Návrhář XAML napsaný v Windows Presentation Foundation (WPF) může být nutné odkazovat jak na Desktop WPF, tak na uživatelském rozhraní návrháře a na podmnožinu WPF, která je součástí programu Silverlight. Stejné sestavení návrháře má přístup k oběma sestavením. Ve výchozím nastavení samostatné odkazy způsobí chybu kompilátoru, protože vazba sestavení uvidí dvě sestavení jako ekvivalentní.  
  
 Možnost kompilátoru **-appconfig** umožňuje určit umístění souboru app.config, který zakáže výchozí chování pomocí `<supportPortability>` značky, jak je znázorněno v následujícím příkladu.  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 Kompilátor předá umístění souboru do logiky vytváření vazeb sestavení CLR.  
  
> [!NOTE]
> Pokud k sestavení aplikace používáte Microsoft Build Engine (MSBuild), můžete nastavit možnost kompilátoru **-appconfig** přidáním značky vlastnosti do souboru. csproj. Chcete-li použít soubor app.config, který je již nastaven v projektu, přidejte `<UseAppConfigForCompiler>` do souboru. csproj značku vlastnosti a nastavte jeho hodnotu na `true` . Chcete-li zadat jiný soubor app.config, přidejte značku vlastnosti `<AppConfigForCompiler>` a nastavte její hodnotu na umístění souboru.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje soubor app.config, který umožňuje aplikaci mít odkazy na implementaci .NET Framework a .NET Framework pro implementaci technologie Silverlight pro jakékoli .NET Framework sestavení, které existuje v obou implementacích. Možnost kompilátoru **-appconfig** určuje umístění tohoto souboru app.config.  
  
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

- [\<supportPortability> Objekt](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [Možnosti kompilátoru C# (abecední pořadí)](./listed-alphabetically.md)
