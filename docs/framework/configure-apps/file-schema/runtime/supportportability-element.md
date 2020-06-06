---
title: Element <supportPortability>
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
ms.openlocfilehash: 63c309a8a93c1d31ed8f73a495cf5154c3590d56
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115658"
---
# <a name="supportportability-element"></a>Element \<supportPortability>
Určuje, že aplikace může odkazovat na stejné sestavení ve dvou různých implementacích .NET Framework tím, že zakáže výchozí chování, které zpracovává sestavení jako ekvivalent pro účely přenositelnosti aplikace.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<supportPortability>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  

Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|PKT|Požadovaný atribut.<br /><br /> Určuje token veřejného klíče pro ovlivněné sestavení jako řetězec.|  
|enabled|Nepovinný atribut.<br /><br /> Určuje, zda by měla být povolena podpora přenositelnosti mezi implementacemi zadaného .NET Framework sestavení.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Description|  
|-----------|-----------------|  
|true|Povolí podporu přenositelnosti mezi implementacemi zadaného .NET Framework sestavení. Toto nastavení je výchozí.|  
|false (nepravda)|Zakažte podporu přenositelnosti mezi implementacemi zadaného .NET Framework sestavení. To umožňuje, aby aplikace měla odkazy na více implementací určeného sestavení.|  
  
### <a name="child-elements"></a>Podřízené elementy  

Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
|`assemblyBinding`|Obsahuje informace o přesměrování verze sestavení a umístění sestavení.|  
  
## <a name="remarks"></a>Poznámky  

Počínaje .NET Framework 4 je podpora automaticky poskytována pro aplikace, které mohou používat jednu ze dvou implementací .NET Framework, například implementaci .NET Framework nebo .NET Framework pro implementaci Silverlight. Dvě implementace konkrétního sestavení .NET Framework jsou v pořadači sestavení zobrazeny jako ekvivalent. V několika scénářích Tato funkce přenositelnosti aplikace způsobuje problémy. V těchto scénářích `<supportPortability>` lze prvek použít k zakázání funkce.  
  
Jedním z takových scénářů je sestavení, které má odkazovat jak na implementaci .NET Framework, tak na .NET Framework pro implementaci Silverlightu konkrétního referenčního sestavení. Například Návrhář XAML napsaný v Windows Presentation Foundation (WPF) může potřebovat odkaz na implementaci WPF Desktop, pro uživatelské rozhraní návrháře a podmnožinu WPF, která je součástí implementace Silverlight. Ve výchozím nastavení samostatné odkazy způsobí chybu kompilátoru, protože vazba sestavení uvidí dvě sestavení jako ekvivalentní. Tento prvek zakáže výchozí chování a umožňuje, aby kompilace proběhla úspěšně.  
  
> [!IMPORTANT]
> Aby mohl kompilátor předat informace do logiky vytváření vazeb sestavení (Common Language Runtime), je nutné použít `/appconfig` možnost kompilátoru k určení umístění souboru App. config, který obsahuje tento prvek.  
  
## <a name="example"></a>Příklad  

Následující příklad umožňuje, aby aplikace měla odkazy na implementaci .NET Framework a .NET Framework pro implementaci technologie Silverlight pro jakékoli .NET Framework sestavení, které existuje v obou implementacích. `/appconfig`Možnost kompilátoru se musí použít k určení umístění tohoto souboru App. config.  
  
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

- [-appconfig (možnosti kompilátoru C#)](../../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- [Přehled sjednocení .NET Framework sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))
