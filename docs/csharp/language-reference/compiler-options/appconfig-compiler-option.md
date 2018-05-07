---
title: -appconfig (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 3fca0821b8665354d840783fca3ab90ece41b2cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-appconfig-c-compiler-options"></a>-appconfig (možnosti kompilátoru C#)
**- Appconfig** – možnost kompilátoru umožňuje aplikaci C# k určení umístění souboru konfigurace (app.config) sestavení aplikace do common language runtime (CLR) v době vazby sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Požadováno. Konfigurační soubor aplikace, který obsahuje nastavení vazby sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Jedno použití **- appconfig** je pokročilé scénáře, ve kterých má sestavení tak, aby odkazovaly na verzi rozhraní .NET Framework a rozhraní .NET Framework pro Silverlight verzi sestavení ve stejnou dobu. Například může mít návrháře XAML napsané v systému Windows Presentation Foundation (WPF) tak, aby odkazovaly na WPF plochu, pro uživatelské rozhraní nástroje designer a do něj podmnožinu WPF, která je součástí Silverlight. Do stejného sestavení návrháře má přístup k obě sestavení. Ve výchozím nastavení odkazy na samostatné způsobit chybu kompilátoru, protože sestavení – vazby vidí dvě sestavení jako ekvivalentní.  
  
 **- Appconfig** – možnost kompilátoru umožňuje určit umístění souboru app.config, která zakáže výchozí chování pomocí `<supportPortability>` značka, jak je znázorněno v následujícím příkladu.  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 Kompilátor předává umístění souboru logiku vazby sestavení modulu CLR.  
  
> [!NOTE]
>  Pokud používáte Microsoft Build Engine (MSBuild) Chcete-li sestavit aplikaci, můžete nastavit **- appconfig** – možnost kompilátoru přidáním vlastnost značku do souboru .csproj. Pokud chcete použít soubor app.config, který je již nastaven v projektu, přidání značka vlastnost `<UseAppConfigForCompiler>` k .csproj souboru a jeho hodnotu nastavte `true`. Zadat soubor app.config jiný, přidejte značku vlastnost `<AppConfigForCompiler>` a jeho hodnotu nastavte na umístění souboru.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje soubor app.config, která umožňuje aplikaci tak, aby měl odkazy na implementace rozhraní .NET Framework a rozhraní .NET Framework pro Silverlight implementaci žádné sestavení rozhraní .NET Framework, který již existuje v obou implementace. **- Appconfig** – možnost kompilátoru Určuje umístění pro tento soubor app.config.  
  
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
 [\<supportPortability – > elementu](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)  
 [Možnosti kompilátoru jazyka C# (abecední pořadí)](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)
