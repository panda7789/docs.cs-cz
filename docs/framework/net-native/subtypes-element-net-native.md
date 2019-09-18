---
title: <Subtypes>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2af1acc02b18c5b97ef66ccae9b70c1f5327bff4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049130"
---
# <a name="subtypes-element-net-native"></a>\<Podtypy > element (.NET Native)
Aplikuje zásady modulu runtime na všechny třídy zděděné z nadřazeného typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Subtypes Activate="policy_type"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type"   
          DataContractSerializer="policy_setting"  
          DataContractJsonSerializer="policy_setting"  
          XmlSerializer="policy_setting"  
          MarshalObject="policy_setting"  
          MarshalDelegate="policy_setting"  
          MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Typ atributu|Popis|  
|---------------|--------------------|-----------------|  
|`Activate`|Reflexe|Nepovinný atribut. Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.|  
|`Browse`|Reflexe|Nepovinný atribut. Řídí dotazování pro informace o prvcích programu, ale nepovoluje přístup za běhu.|  
|`Dynamic`|Reflexe|Nepovinný atribut. Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.|  
|`Serialize`|Serializace|Nepovinný atribut. Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor.|  
|`DataContractSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci, která <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> používá třídu.|  
|`DataContractJsonSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci JSON, které <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> používají třídu.|  
|`XmlSerializer`|Serializace|Nepovinný atribut. Řídí zásady pro serializaci XML, které <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> používají třídu.|  
|`MarshalObject`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů odkazů do prostředí Windows Runtime a COM.|  
|`MarshalDelegate`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.|  
|`MarshalStructure`|Zprostředkovatel komunikace|Nepovinný atribut. Řídí zásady pro zařazování typů hodnot do nativního kódu.|  
  
## <a name="all-attributes"></a>Všechny atributy  
  
|Value|Popis|  
|-----------|-----------------|  
|*policy_setting*|Nastavení, které se má použít u tohoto typu zásad Možné hodnoty jsou `All`, `Auto`, `Excluded` ,`PublicAndInternal`,, ,`Required PublicAndInternal`a. `Required Public` `Public` `Required All` Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Zadejte >](type-element-net-native.md)|Aplikuje zásadu odrazu na typ a všechny jeho členy.|  
  
## <a name="remarks"></a>Poznámky  
 `<Subtypes>` Element použije zásady na všechny podtypy jeho nadřazeného typu. Použijete ji, pokud chcete použít jiné zásady na odvozené typy a jejich základní třídy.  
  
 Atributy Reflection, Serialization a interoperability jsou všechny volitelné, ale musí být přítomné aspoň jedno.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje třídu s názvem `BaseClass` a podtřídou s názvem. `Derived1`  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 Jak je znázorněno v následujícím kódu `Dynamic` , soubor direktiv runtime explicitně nastaví zásady a `Activate` pro `BaseClass` na `Excluded`. Z tohoto důvodu není možné dynamicky vytvářet `BaseClass` instance objektů typu nebo volání `BaseClass` konstruktoru třídy. Element však umožňuje dynamicky vytvářet instance tříd, `BaseClass` které jsou odvozeny z aplikace, a prostřednictvím volání jejich konstruktoru třídy. `<Subtypes>`  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
   <Assembly Name="*Application*" Dynamic="Required All" />  
     <Type Name="Examples.Libraries.BaseClass" Activate ="Excluded" Dynamic="Excluded" >  
        <Subtypes Activate="Public" Dynamic ="Public"/>  
     </Type>  
  </Application>  
</Directives>  
```  
  
 Z `<Subtypes>` důvodu direktivy je následující kód, který dynamicky vytváří `Derived1` instanci <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> instance voláním metody, úspěšně spuštěn.  Bloková proměnná tady je <xref:System.Windows.Controls.TextBlock> objekt v prázdné aplikaci pro Windows Store.  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a>Viz také:

- [\<Typ > element](type-element-net-native.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [Nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md)
