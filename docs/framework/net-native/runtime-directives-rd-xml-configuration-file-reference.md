---
title: "Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2ecfc61c5b586dd3385890d73ded729a38fb41c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a>Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)
Direktivy modulu runtime (. rd.xml) soubor je konfigurační soubor XML, který určuje, zda jsou k dispozici pro reflexi prvky určené programu. Tady je příklad souboru direktivy modulu runtime:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
<Application>  
  <Namespace Name="Contoso.Cloud.AppServices" Serialize="Required Public" />  
  <Namespace Name="ContosoClient.ViewModels" Serialize="Required Public" />  
  <Namespace Name="ContosoClient.DataModel" Serialize="Required Public" />  
  <Namespace Name="Contoso.Reader.UtilityLib" Serialize="Required Public" />  
  
  <Namespace Name="System.Collections.ObjectModel" >  
    <TypeInstantiation Name="ObservableCollection"   
          Arguments="ContosoClient.DataModel.ProductItem" Serialize="Public" />  
    <TypeInstantiation Name="ReadOnlyObservableCollection"   
          Arguments="ContosoClient.DataModel.ProductGroup" Serialize="Public" />  
  </Namespace>  
</Application>  
</Directives>  
```  
  
## <a name="the-structure-of-a-runtime-directives-file"></a>Struktura souboru direktivy modulu runtime  
 Direktivy modulu runtime souborů používá `http://schemas.microsoft.com/netfx/2013/01/metadata` oboru názvů.  
  
 Kořenový element [direktivy](../../../docs/framework/net-native/directives-element-net-native.md) elementu. Může obsahovat nula nebo více [knihovny](../../../docs/framework/net-native/library-element-net-native.md) prvky a nula nebo jedna [aplikace](../../../docs/framework/net-native/application-element-net-native.md) elementu, jak je znázorněno v následující strukturu. Atributy [aplikace](../../../docs/framework/net-native/application-element-net-native.md) element můžete definovat zásady reflexe modulu runtime celou aplikaci, nebo může sloužit jako kontejner pro podřízené elementy. [Knihovny](../../../docs/framework/net-native/library-element-net-native.md) elementu, na druhé straně je jednoduše kontejner. Podřízené objekty daného [aplikace](../../../docs/framework/net-native/application-element-net-native.md) a [knihovny](../../../docs/framework/net-native/library-element-net-native.md) elementy definovat typy, metody, pole, vlastnosti a události, které jsou k dispozici pro reflexi.  
  
 Referenční informace, vyberte elementy z následující strukturu nebo najdete v části [elementy direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-elements.md). V následující hierarchie se třemi tečkami označí rekurzivní struktury. Informace v závorkách označuje, zda je daný element požadované nebo volitelné a pokud se používá, kolik instance (jeden nebo více) jsou povoleny.  
  
 [Direktivy](../../../docs/framework/net-native/directives-element-net-native.md) [1:1]  
 [Aplikace](../../../docs/framework/net-native/application-element-net-native.md) [0:1]  
 [Sestavení](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]  
 [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]  
 . . .  
 [Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 . . .  
 [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (sestavený obecného typu) [0:M]  
 . . .  
 [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]  
 [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]  
 . . .  
 [Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 . . .  
 [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (sestavený obecného typu) [0:M]  
 . . .  
 [Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 [Podtypů](../../../docs/framework/net-native/subtypes-element-net-native.md) (podtřídy obsahující typu) [O:1]  
 [Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 . . .  
 [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (sestavený obecného typu) [0:M]  
 . . .  
 [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (obsahující typ je atribut) [O:1]  
 [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]  
 [Metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M]  
 [Parametr](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]  
 [TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]  
 [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]  
 [MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (sestavený obecná metoda) [0:M]  
 [Vlastnost](../../../docs/framework/net-native/property-element-net-native.md) [0:M]  
 [Pole](../../../docs/framework/net-native/field-element-net-native.md) [0:M]  
 [Událost](../../../docs/framework/net-native/event-element-net-native.md) [0:M]  
 [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (sestavený obecného typu) [0:M]  
 [Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 . . .  
 [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (sestavený obecného typu) [0:M]  
 . . .  
 [Metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M]  
 [Parametr](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]  
 [TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]  
 [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]  
 [MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (sestavený obecná metoda) [0:M]  
 [Vlastnost](../../../docs/framework/net-native/property-element-net-native.md) [0:M]  
 [Pole](../../../docs/framework/net-native/field-element-net-native.md) [0:M]  
 [Událost](../../../docs/framework/net-native/event-element-net-native.md) [0:M]  
 [Knihovna](../../../docs/framework/net-native/library-element-net-native.md) [0:M]  
 [Sestavení](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]  
 [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]  
 . . .  
 [Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 . . .  
 [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (sestavený obecného typu) [0:M]  
 . . .  
 [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]  
 [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]  
 . . .  
 [Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 . . .  
 [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (sestavený obecného typu) [0:M]  
 . . .  
 [Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 [Podtypů](../../../docs/framework/net-native/subtypes-element-net-native.md) (podtřídy obsahující typu) [O:1]  
 [Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 . . .  
 [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (sestavený obecného typu) [0:M]  
 . . .  
 [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (obsahující typ je atribut) [O:1]  
 [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]  
 [Metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M]  
 [MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (sestavený obecná metoda) [0:M]  
 [Vlastnost](../../../docs/framework/net-native/property-element-net-native.md) [0:M]  
 [Pole](../../../docs/framework/net-native/field-element-net-native.md) [0:M]  
 [Událost](../../../docs/framework/net-native/event-element-net-native.md) [0:M]  
 [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (sestavený obecného typu) [0:M]  
 [Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 . . .  
 [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (sestavený obecného typu) [0:M]  
 . . .  
 [Metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M]  
 [MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (sestavený obecná metoda) [0:M]  
 [Vlastnost](../../../docs/framework/net-native/property-element-net-native.md) [0:M]  
 [Pole](../../../docs/framework/net-native/field-element-net-native.md) [0:M]  
 [Událost](../../../docs/framework/net-native/event-element-net-native.md) [0:M]  
  
 [Aplikace](../../../docs/framework/net-native/application-element-net-native.md) element může mít žádné atributy, nebo můžete mít atributy zásad popsané v [Runtime – direktiva a zásady části](#Directives).  
  
 A [knihovny](../../../docs/framework/net-native/library-element-net-native.md) element má jeden atribut, `Name`, který určuje název sestavení, bez jeho přípona souboru nebo knihovny. Například následující [knihovny](../../../docs/framework/net-native/library-element-net-native.md) element se vztahuje na sestavení s názvem Extensions.dll.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <!-- Child elements go here -->    
  </Application>  
  <Library Name="Extensions">  
     <!-- Child elements go here -->    
  </Library>  
</Directives>  
```  
  
<a name="Directives"></a>   
## <a name="runtime-directives-and-policy"></a>Direktivy modulu runtime a zásady  
 [Aplikace](../../../docs/framework/net-native/application-element-net-native.md) elementu samotnému a podřízených elementů [knihovny](../../../docs/framework/net-native/library-element-net-native.md) a [aplikace](../../../docs/framework/net-native/application-element-net-native.md) elementy vyjádření zásad; to znamená, že definují způsob, ve kterém můžete použít aplikaci reflexe do programu elementu. Typ zásad je definován atribut elementu (například `Serialize`). Hodnota zásady je definován hodnotou atributu (například `Serialize="Required"`).  
  
 Žádné zásady určeného atribut elementu se vztahuje na všechny podřízené prvky, které nezadávejte hodnotu pro tuto zásadu. Například, pokud je zadána zásadu [typ](../../../docs/framework/net-native/type-element-net-native.md) elementu, které zásady platí pro všechny obsažené typy a členy, pro které není explicitně zadané zásady.  
  
 Zásady, které může být vyjádřená [aplikace](../../../docs/framework/net-native/application-element-net-native.md), [sestavení](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [ Podtypů](../../../docs/framework/net-native/subtypes-element-net-native.md), a [typ](../../../docs/framework/net-native/type-element-net-native.md) elementy se liší od zásad, který může být vyjádřený pro jednotlivé členy (pomocí [metoda](../../../docs/framework/net-native/method-element-net-native.md), [vlastnost](../../../docs/framework/net-native/property-element-net-native.md), [Pole](../../../docs/framework/net-native/field-element-net-native.md), a [událostí](../../../docs/framework/net-native/event-element-net-native.md) elementy).  
  
### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a>Určení zásad pro sestavení, obory názvů a typy  
 [Aplikace](../../../docs/framework/net-native/application-element-net-native.md), [sestavení](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [podtypů](../../../docs/framework/net-native/subtypes-element-net-native.md)a [ Typ](../../../docs/framework/net-native/type-element-net-native.md) elementy podporují tyto typy zásad:  
  
-   `Activate`. Ovládací prvky runtime přístup k konstruktory, chcete-li povolit aktivace instancí.  
  
-   `Browse`. Ovládací prvky dotazování na informace o programu elementů, ale nepovolí žádné přístup k modulu runtime.  
  
-   `Dynamic`. Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktory, metody, polí, vlastnosti a události, chcete-li povolit dynamické programování.  
  
-   `Serialize`. Ovládací prvky runtime přístup k konstruktory, pole a vlastnosti, aby instance typu serializovat a serializovat knihovny třetích stran, jako je například serializátor Newtonsoft JSON.  
  
-   `DataContractSerializer`. Zásady pro serializaci, který používá ovládací prvky <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.  
  
-   `DataContractJsonSerializer`. Zásady pro serializaci JSON, který používá ovládací prvky <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.  
  
-   `XmlSerializer`. Zásady pro serializaci XML, který používá ovládací prvky <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.  
  
-   `MarshalObject`. Ovládací prvky zásady pro zařazování odkazové typy WinRT a COM.  
  
-   `MarshalDelegate`. Ovládací prvky zásady pro zařazování delegáta typy jako ukazatelů na funkce do nativního kódu.  
  
-   `MarshalStructure` . Ovládací prvky zásady pro zařazování struktur nativního kódu.  
  
 Jsou nastavení související s těmito typy zásad:  
  
-   `All`. Povolení zásad pro všechny typy a členy, kteří řetězu nástroj nedojde k odebrání.  
  
-   `Auto`. Použije výchozí chování. (Není zadávání zásad je stejné jako nastavení zásad na `Auto` Pokud tuto zásadu je přepsat, například nadřazeného elementu.)  
  
-   `Excluded`. Zakažte zásadu pro element programu.  
  
-   `Public`. Povolte zásady pro veřejné typy nebo členy, pokud řetězu nástroj zjistí, že člen není nutný a proto ji odstraní. (V takovém případě je nutné použít `Required Public` zajistit, že člen se ukládají a má reflexe možnosti.)  
  
-   `PublicAndInternal`. Zásady pro veřejné a interní typy nebo členy povolte, pokud nástroj řetězu neodstraní.  
  
-   `Required Public`. Vyžadovat řetězu nástroj zachovat veřejných typů a členů, jestli se používají a povolíte zásady pro ně.  
  
-   `Required PublicAndInternal`. Vyžadovat řetězu nástroj aby veřejné a interní typy a členy, jestli se používají a povolíte zásady pro ně.  
  
-   `Required All`. Vyžadovat řetězu nástroj chránit všechny typy a členy, jestli se používají a povolíte zásady pro ně.  
  
 Například následující soubor direktivy modulu runtime definuje zásady pro všechny typy a členy v sestavení DataClasses.dll. Umožňuje reflexe pro serializaci všechny veřejné vlastnosti umožňuje procházení pro všechny typy a členy typu umožňuje aktivace pro všechny typy (z důvodu `Dynamic` atribut) a umožňuje reflexe pro všechny veřejné typy a členy.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public"   
                Browse="All" Activate="PublicAndInternal"   
                Dynamic="Public"  />  
   </Application>  
   <Library Name="UtilityLibrary">  
     <!-- Child elements go here -->    
   </Library>  
</Directives>  
```  
  
### <a name="specifying-policy-for-members"></a>Určení zásad pro členy  
 [Vlastnost](../../../docs/framework/net-native/property-element-net-native.md) a [pole](../../../docs/framework/net-native/field-element-net-native.md) elementy podporují tyto typy zásad:  
  
-   `Browse`– Ovládací prvky dotazování na informace o tomto členu, ale nepovolí žádné přístup k modulu runtime.  
  
-   `Dynamic`-Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktory, metody, polí, vlastnosti a události, chcete-li povolit dynamické programování. Určuje také dotazování na informace o nadřazeném typu.  
  
-   `Serialize`-Řídí runtime přístup k člen instance typu serializovat a deserializovat pomocí knihovny například serializátor Newtonsoft JSON povolit. Tuto zásadu lze použít k konstruktory, polí a vlastností.  
  
 [Metoda](../../../docs/framework/net-native/method-element-net-native.md) a [událostí](../../../docs/framework/net-native/event-element-net-native.md) elementy podporují tyto typy zásad:  
  
-   `Browse`– Ovládací prvky dotazování na informace o tomto členu, ale neumožňuje přístup za běhu.  
  
-   `Dynamic`-Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktory, metody, polí, vlastnosti a události, chcete-li povolit dynamické programování. Určuje také dotazování na informace o nadřazeném typu.  
  
 Jsou nastavení související s těmito typy zásad:  
  
-   `Auto`-Použijte výchozí chování. (Není zadávání zásad je stejné jako nastavení zásad na `Auto` Pokud něco ho přepíše.)  
  
-   `Excluded`-Nikdy obsahovat metadata pro člena.  
  
-   `Included`-Povolte zásady, pokud nadřazený typ nachází ve výstupu.  
  
-   `Required`-Vyžadují řetězu nástroj zachovat tento člen i když se zobrazí na nevyužitá a povolíte zásady pro ni.  
  
## <a name="runtime-directives-file-semantics"></a>Sémantika souboru direktivy modulu runtime  
 Zásady lze definovat současně pro elementy vyšší úrovně a nižší úrovni. Například zásad lze definovat pro sestavení a některé typy obsažené v této sestavě. Pokud není uvedeno konkrétní prvek nižší úrovně, dědí zásady svého nadřazeného objektu. Například pokud `Assembly` nachází element ale `Type` elementy nejsou, zásady zadaný v `Assembly` element platí pro jednotlivé typy v sestavení. Zásady pro stejného elementu programu můžete taky použít několik elementů. Například samostatné [sestavení](../../../docs/framework/net-native/assembly-element-net-native.md) elementy může stejného elementu zásad definovat pro stejného sestavení jinak. Následující části popisují, jak zásady pro konkrétní typ vyřešen v těchto případech.  
  
 A [typ](../../../docs/framework/net-native/type-element-net-native.md) nebo [metoda](../../../docs/framework/net-native/method-element-net-native.md) element obecný typ nebo metoda svých zásad platí pro všechny konkretizací, které nemají své vlastní zásady. Například `Type` element, který určuje zásady pro <xref:System.Collections.Generic.List%601> vztahuje na všechny zkonstruovaná instance daného obecného typu, pokud není přepsána pro konkrétní sestavený obecného typu (například `List<Int32>`) podle `TypeInstantiation` element. Elementy, jinak hodnota definovat zásady pro element program s názvem.  
  
 Pokud element je nejednoznačné, modul hledá shody a pokud najde přesnou shodu, použije ho. Pokud najde více shod, budou existovat upozornění nebo chyby.  
  
### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a>Pokud dva direktivy uplatňovat zásady na stejný element programu  
 Pokud dva elementy v soubory direktivy modulu runtime jinou zkuste nastavit stejného typu zásady pro stejného elementu program (například sestavení nebo typ) na různé hodnoty, konflikt vyřešen následujícím způsobem:  
  
1.  Pokud `Excluded` element přítomen, vyšší prioritu.  
  
2.  `Required`má vyšší prioritu více není `Required`.  
  
3.  `All`má vyšší prioritu než `PublicAndInternal`, který má vyšší prioritu než `Public`.  
  
4.  Explicitní nastavení, má vyšší prioritu než `Auto`.  
  
 Například pokud projekt obsahuje následující dva soubory direktivy modulu runtime, zásady serializace pro DataClasses.dll je nastavené na obojí `Required Public` a `All`. V takovém případě by možné přeložit jako zásady serializace `Required All`.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public"/>  
   </Application>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="All" />  
   </Application>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
 Ale pokud dva direktivy v souboru direktivy modulu runtime jeden zkuste nastavit stejný typ zásady pro stejného elementu programu, nástroj definice schématu XML zobrazí chybovou zprávu.  
  
### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a>Pokud podřízenými a nadřazenými prvky použít stejný typ zásad  
 Podřízené elementy přepsat své nadřazené elementy, včetně `Excluded` nastavení. Přepsání je hlavním důvodem by chcete určit `Auto`.  
  
 V následujícím příkladu, nastavení pro všechno, co v zásad serializace `DataClasses` , není v `DataClasses.ViewModels` by `Required Public`a vše, co je v obou `DataClasses` a `DataClasses.ViewModels` by `All`.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public" >  
         <Namespace Name="DataClasses.ViewModels" Seralize="All" />  
      </Assembly>  
   </Appliction>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a>Pokud otevřete obecné typy a instancí elementy použít stejný typ zásad  
 V následujícím příkladu `Dictionary<int,int>` je přiřazen `Browse` zásady pouze v případě, že modul je další důvod, jí přidělit `Browse` zásad (které by jinak byly výchozí chování); každých vytváření instancí z <xref:System.Collections.Generic.Dictionary%602> budou mít všechny Procházet její členy.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public" >  
         <Namespace Name="DataClasses.ViewModels" Seralize="All" />  
      </Assembly>  
      <Namespace Name="DataClasses.Generics" />  
      <Type Name="Dictionary" Browse="All" />  
      <TypeInstantiation Name="Dictionary"   
                         Arguments="System.Int32,System.Int32" Browse="Auto" />  
   </Application>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
### <a name="how-policy-is-inferred"></a>Jak odvodit zásad  
 Každý typ zásad má jinou sadu pravidel, které určují, jak ovlivňuje přítomnosti tohoto typu zásad jiných objektů.  
  
#### <a name="the-effect-of-browse-policy"></a>Účinku zásad procházení  
 Použití `Browse` zásadu k typu zahrnuje následující změny zásad:  
  
-   Základní typ typu je označené jako `Browse` zásad.  
  
-   Pokud je typ instancí obecného, je označené jako bez instancí verzi typ `Browse` zásad.  
  
-   Pokud je typ s delegátem, `Invoke` je označené jako metodu na typ `Dynamic` zásad.  
  
-   Každé rozhraní typu je označené jako `Browse` zásad.  
  
-   Typ každý atribut použitý typ je označené jako `Browse` zásad.  
  
-   Pokud je obecný typ, je označené jako každý typ omezení `Browse` zásad.  
  
-   Pokud je obecný typ, jsou označené jako typy, po které je vytvořena instance typu `Browse` zásad.  
  
 Použití `Browse` zásad na metodu zahrnuje následující změny zásad:  
  
-   Každý typ parametru metody, je označené jako `Browse` zásad.  
  
-   Návratový typ metody je označené jako `Browse` zásad.  
  
-   Obsahující typ metody je označené jako `Browse` zásad.  
  
-   Pokud je metoda vytvořenou instanci obecné metody, je označené jako bez instancí obecná metoda `Browse` zásad.  
  
-   Typ každý atribut použitý metodu je označené jako `Browse` zásad.  
  
-   Pokud je metoda Obecné, je označené jako každý typ omezení `Browse` zásad.  
  
-   Pokud je metoda Obecné, jsou označené jako typy, po které je vytvořena instance metodu `Browse` zásad.  
  
 Použití `Browse` zásady pro pole zahrnuje následující změny zásad:  
  
-   Typ každý atribut použitých pro pole je označené jako `Browse` zásad.  
  
-   Typ pole je označené jako `Browse` zásad.  
  
-   Typ, do které patří pole je označené jako `Browse` zásad.  
  
#### <a name="the-effect-of-dynamic-policy"></a>Účinek zásady dynamického  
 Použití `Dynamic` zásadu k typu zahrnuje následující změny zásad:  
  
-   Základní typ typu je označené jako `Dynamic` zásad.  
  
-   Pokud je typ instancí obecného, je označené jako bez instancí verzi typ `Dynamic` zásad.  
  
-   Pokud je typ typem delegáta `Invoke` je označené jako metodu na typ `Dynamic` zásad.  
  
-   Každé rozhraní typu je označené jako `Browse` zásad.  
  
-   Typ každý atribut použitý typ je označené jako `Browse` zásad.  
  
-   Pokud je obecný typ, je označené jako každý typ omezení `Browse` zásad.  
  
-   Pokud je obecný typ, jsou označené jako typy, po které je vytvořena instance typu `Browse` zásad.  
  
 Použití `Dynamic` zásad na metodu zahrnuje následující změny zásad:  
  
-   Každý typ parametru metody, je označené jako `Browse` zásad.  
  
-   Návratový typ metody je označené jako `Dynamic` zásad.  
  
-   Obsahující typ metody je označené jako `Dynamic` zásad.  
  
-   Pokud je metoda vytvořenou instanci obecné metody, je označené jako bez instancí obecná metoda `Browse` zásad.  
  
-   Typ každý atribut použitý metodu je označené jako `Browse` zásad.  
  
-   Pokud je metoda Obecné, je označené jako každý typ omezení `Browse` zásad.  
  
-   Pokud je metoda Obecné, jsou označené jako typy, po které je vytvořena instance metodu `Browse` zásad.  
  
-   Můžete vyvolat metodu `MethodInfo.Invoke`, a že bude možné ve vytváření delegáta <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.  
  
 Použití `Dynamic` zásady pro pole zahrnuje následující změny zásad:  
  
-   Typ každý atribut použitých pro pole je označené jako `Browse` zásad.  
  
-   Typ pole je označené jako `Dynamic` zásad.  
  
-   Typ, do které patří pole je označené jako `Dynamic` zásad.  
  
#### <a name="the-effect-of-activation-policy"></a>Účinek Zásady aktivace  
 Použití zásad aktivace typu zahrnuje následující změny zásad:  
  
-   Pokud je typ instancí obecného, je označené jako bez instancí verzi typ `Browse` zásad.  
  
-   Pokud je typ typem delegáta `Invoke` je označené jako metodu na typ `Dynamic` zásad.  
  
-   Konstruktory typu jsou označené jako `Activation` zásad.  
  
 Použití `Activation` zásad na metodu zahrnuje následující změny zásad:  
  
-   Může vyvolat konstruktor <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> a <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> metody. Pro metody `Activation` zásada ovlivňuje pouze konstruktory.  
  
 Použití `Activation` zásada pro pole nemá žádný vliv.  
  
#### <a name="the-effect-of-serialize-policy"></a>Účinku zásad serializace  
 `Serialize` Zásad umožňuje použití běžné serializátorů prostřednictvím reflexe. Nicméně, protože vzory přístupu k přesný odraz z jiných společností než Microsoft serializátorů nejsou známé společnosti Microsoft, nemusí být tato zásada zcela efektivní.  
  
 Použití `Serialize` zásadu k typu zahrnuje následující změny zásad:  
  
-   Základní typ typu je označené jako `Serialize` zásad.  
  
-   Pokud je typ instancí obecného, je označené jako bez instancí verzi typ `Browse` zásad.  
  
-   Pokud je typ typem delegáta `Invoke` je označené jako metodu na typ `Dynamic` zásad.  
  
-   Pokud je typ výčtu, je označené pole typu `Serialize` zásad.  
  
-   Pokud typ implementuje <xref:System.Collections.Generic.IEnumerable%601>, `T` označena `Serialize` zásad.  
  
-   Pokud je typ <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, nebo <xref:System.Collections.Generic.IReadOnlyList%601>, pak `T[]` a <xref:System.Collections.Generic.List%601> označené jako `Serialize` zásady, ale žádní členové typu rozhraní jsou označené `Serialize`zásad.  
  
-   Pokud je typ <xref:System.Collections.Generic.List%601>, žádné členy typu jsou označené jako `Serialize` zásad.  
  
-   Pokud je typ <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> označena `Serialize` zásad. žádné členy typu jsou označené, ale `Serialize` zásad.  
  
-   Pokud je typ <xref:System.Collections.Generic.Dictionary%602>, žádné členy typu jsou označené jako `Serialize` zásad.  
  
-   Pokud typ implementuje <xref:System.Collections.Generic.IDictionary%602>, `TKey` a `TValue` jsou označené `Serialize` zásad.  
  
-   Každý konstruktor, každý přistupujícího objektu vlastnosti a každé pole je označené `Serialize` zásad.  
  
 Použití `Serialize` zásad na metodu zahrnuje následující změny zásad:  
  
-   Typ obsahující je označené jako `Serialize` zásad.  
  
-   Návratový typ metody je označené jako `Serialize` zásad.  
  
 Použití `Serialize` zásady pro pole zahrnuje následující změny zásad:  
  
-   Typ obsahující je označené jako `Serialize` zásad.  
  
-   Typ pole je označené jako `Serialize` zásad.  
  
#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserialier-policies"></a>Účinek zásady XmlSerializer, DataContractSerializer a DataContractJsonSerialier  
 Na rozdíl od `Serialize` zásadu, která je určena na základě reflexe serializátorů, `XmlSerializer`, `DataContractSerializer`, a `DataContractJsonSerializer` zásady slouží k povolení sadu serializátorů, které jsou známé [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězu. Tyto serializátorů nejsou implementované pomocí reflexe, ale sadu typů, které může být serializovány v době běhu je určen podobným způsobem jako typy, které jsou reflectable.  
  
 Použití jednu z těchto zásad na typ umožňuje typ k serializaci s odpovídající serializátor. Všechny typy, které pro Serializační stroj můžete určit staticky potřebují serializace bude také být serializovatelný.  
  
 Tyto zásady mají vliv na metody nebo pole.  
  
 Další informace najdete v části "Rozdíly v Serializátorů" v [migrace vaše aplikace pro Windows Store do .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md).  
  
## <a name="see-also"></a>Viz také  
 [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Reflexe a .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)
