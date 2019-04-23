---
title: Element <supportPortability>
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cc26f9721e911e05c5b5d4092be21a4e1191c84
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183938"
---
# <a name="supportportability-element"></a>\<supportPortability > – Element
Určuje, že aplikace může odkazovat na stejné sestavení ve dvou různých implementacích rozhraní .NET Framework zakázáním výchozího chování, které považuje za ekvivalent pro účely přenositelnosti aplikace sestavení.  
  
 \<Konfigurace > – Element  
\<modul runtime > – Element  
\<assemblybinding – > – Element  
\<supportPortability > – Element  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|PKT|Požadovaný atribut.<br /><br /> Určuje token veřejného klíče dotčeného sestavení jako řetězec.|  
|Povoleno|Nepovinný atribut.<br /><br /> Určuje, zda by měla být povolena podpora pro přenositelnost mezi implementacemi zadaného sestavení rozhraní .NET Framework.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|true|Povolte podporu pro přenositelnost mezi implementacemi zadaného sestavení rozhraní .NET Framework. Toto nastavení je výchozí.|  
|false|Zakažte podporu pro přenositelnost mezi implementacemi zadaného sestavení rozhraní .NET Framework. To umožňuje aplikaci mít odkazy na více implementací zadaného sestavení.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
|`assemblyBinding`|Obsahuje informace o přesměrování verze sestavení a umístění sestavení.|  
  
## <a name="remarks"></a>Poznámky  
 Počínaje [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], podpora je poskytována automaticky pro aplikace, které můžete použít jednu ze dvou implementací rozhraní .NET Framework, například pro implementaci rozhraní .NET Framework nebo .NET Framework pro implementaci Silverlight. Tyto dvě implementace konkrétního sestavení rozhraní .NET Framework jsou vázacím objektem sestavení považovány za ekvivalentní. V několika scénářích tato funkce přenositelnosti aplikace způsobuje problémy. V těchto případech `<supportPortability>` elementu je možné zakázat funkci.  
  
 Jeden takový scénář je sestavení, které musí odkazovat implementaci rozhraní .NET Framework a .NET Framework pro implementaci Silverlight sestavení. Například Návrhář XAML, zapsán ve Windows Presentation Foundation (WPF) může být nutné odkazovat oba WPF plochy implementace, návrháře uživatelské rozhraní a na podmnožinu WPF, která je součástí implementace Silverlight. Ve výchozím nastavení samostatné odkazy zapříčiní chybu kompilátoru, protože vazba sestavení chápe daná dvě sestavení jako ekvivalentní. Tento prvek zakazuje výchozí chování a umožňuje, aby kompilace proběhla úspěšně.  
  
> [!IMPORTANT]
>  Aby kompilátor mohl předat informace pro vytváření vazeb sestavení logiky common language runtime, je nutné použít `/appconfig` – možnost kompilátoru k určení umístění souboru app.config, který obsahuje tento element.  
  
## <a name="example"></a>Příklad  
 Následující příklad umožňuje aplikaci mít odkazy na implementaci rozhraní .NET Framework a .NET Framework pro implementaci Silverlight žádné sestavení rozhraní .NET Framework, která existuje v obou implementacích. `/appconfig` Kompilátoru možnost musí být použita ke specifikaci umístění tohoto app.config souboru.  
  
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

- [/ appconfig (možnosti kompilátoru C#)](../../../../../docs/csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- [Přehled sjednocení sestavení rozhraní .NET framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))
