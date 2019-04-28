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
ms.openlocfilehash: 102ed3977d56ace0dab63b1f066cc10a6fc5dfbf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663060"
---
# <a name="-appconfig-c-compiler-options"></a>-appconfig (možnosti kompilátoru C#)
**- Appconfig** – možnost kompilátoru umožňuje aplikaci v C# k určení umístění sestavení aplikace konfiguračního souboru (app.config) do common language runtime (CLR) v době vazby sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Povinný parametr. Konfigurační soubor aplikace obsahující nastavení vazeb sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Jedno použití **- appconfig** je pokročilé scénáře, ve kterých má sestavení tak, aby odkazovaly na verzi rozhraní .NET Framework a .NET Framework programu Silverlight daného sestavení ve stejnou dobu. Například Návrhář XAML, zapsán ve Windows Presentation Foundation (WPF) pravděpodobně tak, aby odkazovaly na WPF plochu, pro návrháře uživatelské rozhraní a na podmnožinu WPF, která je součástí Silverlightu. Stejného návrháře sestavení má přístup k obě sestavení. Ve výchozím nastavení samostatné odkazy zapříčiní chybu kompilátoru, protože vazba sestavení chápe daná dvě sestavení jako ekvivalentní.  
  
 **- Appconfig** – možnost kompilátoru umožňuje určit umístění souboru app.config, který zakazuje výchozí chování pomocí `<supportPortability>` označit, jak je znázorněno v následujícím příkladu.  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 Kompilátor předá umístění souboru modulu CLR vytváření vazeb sestavení logiky.  
  
> [!NOTE]
>  Pokud používáte Microsoft Build Engine (MSBuild) k sestavení aplikace, můžete nastavit **- appconfig** – možnost kompilátoru přidáním tag vlastnosti do souboru csproj. Použití souboru app.config, který je již nastaven v projektu, přidejte vlastnost značku `<UseAppConfigForCompiler>` do souboru .csproj souboru a nastavte jej na hodnotu `true`. K určení různých app.config soubor, přidejte vlastnost značku `<AppConfigForCompiler>` a nastavení jeho hodnoty k umístění souboru.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje soubor app.config, který umožňuje aplikaci mít odkazy na implementaci rozhraní .NET Framework a .NET Framework pro implementaci Silverlight žádné sestavení rozhraní .NET Framework, která existuje v obou implementacích. **- Appconfig** – možnost kompilátoru Určuje umístění tohoto app.config souboru.  
  
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

- [\<supportPortability > – Element](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [Možnosti kompilátoru jazyka C# (abecední pořadí)](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)
