---
title: "x:Uid – direktiva"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
caps.latest.revision: "12"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9abd4a1851ce21a1858f51ff4ce42998c20639e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="xuid-directive"></a>x:Uid – direktiva
Poskytuje jedinečný identifikátor pro prvky značek. V mnoha scénářích tohoto jedinečného identifikátoru je používán procesy lokalizace XAML a nástroje.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object x:Uid="identifier"... />  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`identifier`|A vytvořit ručně nebo automaticky vygenerovanou řetězec, který by měl být jedinečný v souboru v případě je interpretována `x:Uid` příjemce.|  
  
## <a name="remarks"></a>Poznámky  
 V [MS-XAML] `x:Uid` je definován jako direktivu. Další informace najdete v tématu [ \[MS-XAML\] části 5.3.6](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
 `x:Uid`je diskrétní z `x:Name` i z důvodu stanovené scénář lokalizace XAML a tak, aby identifikátory, které se používají pro lokalizaci žádné závislosti na programovací model důsledky `x:Name`. Navíc `x:Name` se řídí XAML namescope; však `x:Uid` není řídí všechny XAML jazyk definované konceptu vynucení jedinečnosti. XAML procesorů v širokém smyslu (procesory, které nejsou součástí procesu lokalizace) neočekává vynutit jedinečnosti `x:Uid` hodnoty. Zda je odpovědnost koncepčně na původce hodnot. Očekávání jedinečnosti `x:Uid` hodnot v rámci jednoho zdroje XAML je možné logicky pro spotřebitele hodnot, jako jsou nástroje nebo vyhrazené globalizace procesy. Typické jedinečnosti modelu je, že `x:Uid` hodnoty jsou jedinečné v rámci soubor kódováním XML, který představuje XAML.  
  
 Nástroje, které mají důležité informace o konkrétní schématu XAML můžete použít `x:Uid` pouze pro hodnotu true možnosti lokalizace řetězce, místo ve všech případech, kde se vyskytuje textovou hodnotu řetězce v kódu.  
  
 Rozhraní můžete zadat konkrétní vlastnosti v jejich objektový model jako alias pro `x:Uid` použitím atribut <xref:System.Windows.Markup.UidPropertyAttribute> definující typu. Pokud rozhraní určuje konkrétní vlastnosti, není platné. Chcete-li zadat oba seznamy `x:Uid` a člen alias na stejný objekt. Pokud oba `x:Uid` a jsou zadaný člen alias, rozhraní .NET Framework XAML Services API obvykle vyvolá <xref:System.Xaml.XamlDuplicateMemberException> pro tento případ.  
  
## <a name="wpf-usage-notes"></a>Poznámky pro použití WPF  
 Další informace o roli `x:Uid` v procesu lokalizace WPF a ve formě BAML XAML najdete v části [globalizace pro grafický subsystém WPF](../../../docs/framework/wpf/advanced/globalization-for-wpf.md) nebo<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
 <xref:Microsoft.Build.Tasks.Windows.UidManager>  
 [Globalizace pro WPF](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
