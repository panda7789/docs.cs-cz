---
title: RelativeSource MarkupExtension
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ea5d269c3d455a4fbe3a34dca4335e0d8999d80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="relativesource-markupextension"></a>RelativeSource MarkupExtension
Určuje vlastnosti <xref:System.Windows.Data.RelativeSource> vazby zdroj, který se má použít v rámci [vazba – rozšíření značek](../../../../docs/framework/wpf/advanced/binding-markup-extension.md), nebo při nastavení <xref:System.Windows.Data.Binding.RelativeSource%2A> vlastnost <xref:System.Windows.Data.Binding> element navázat v jazyce XAML.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xml  
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>  
```  
  
## <a name="xaml-attribute-usage-nested-within-binding-extension"></a>Použití atributu XAML (vnořeného do rozšíření Binding)  
  
```xml  
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML  
  
```xml  
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource Mode="modeEnumValue"/>  
  </Binding.RelativeSource>  
</Binding>  
- or   
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource  
      Mode="FindAncestor"  
      AncestorType="{x:Type typeName}"  
      AncestorLevel="intLevel"  
    />  
  </Binding.RelativeSource>  
</Binding>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`modeEnumValue`|Jeden z následujících postupů:<br /><br /> -Token řetězec `Self`; odpovídá <xref:System.Windows.Data.RelativeSource> jako vytvořit s jeho <xref:System.Windows.Data.RelativeSource.Mode%2A> vlastnost nastavena na hodnotu <xref:System.Windows.Data.RelativeSourceMode.Self>.<br />-Token řetězec `TemplatedParent`; odpovídá <xref:System.Windows.Data.RelativeSource> jako vytvořit s jeho <xref:System.Windows.Data.RelativeSource.Mode%2A> vlastnost nastavena na hodnotu <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.<br />-Token řetězec `PreviousData`; odpovídá <xref:System.Windows.Data.RelativeSource> jako vytvořit s jeho <xref:System.Windows.Data.RelativeSource.Mode%2A> vlastnost nastavena na hodnotu <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.<br />-Níže najdete informace v `FindAncestor` režimu.|  
|`FindAncestor`|Token řetězec `FindAncestor`. Pomocí tohoto tokenu přejde do režimu které `RelativeSource` Určuje typ nadřazené a volitelně nadřazené úrovni. To odpovídá <xref:System.Windows.Data.RelativeSource> jako vytvořit s jeho <xref:System.Windows.Data.RelativeSource.Mode%2A> vlastnost nastavena na hodnotu <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.|  
|`typeName`|Vyžaduje se pro `FindAncestor` režimu. Název typu, který vyplní celé <xref:System.Windows.Data.RelativeSource.AncestorType%2A> vlastnost.|  
|`intLevel`|Volitelné pro `FindAncestor` režimu. Úroveň předchůdce (vyhodnocována ve směru nadřazeného uzlu v logickém stromu)|  
  
## <a name="remarks"></a>Poznámky  
 `{RelativeSource TemplatedParent}`použití vazby jsou klíče technik, které řeší větší koncept oddělení ovládacího prvku uživatelského rozhraní a logiku ovládacího prvku. To umožňuje vytvořit vazbu z definice šablony na nadřazený objekt vytvořený pomocí šablony (instanci objektu vytvořenou za běhu, pro niž je šablona použita). Pro tento případ [TemplateBinding – rozšíření značek](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) ve skutečnosti je sdružená vlastnost pro následující výraz vazby: `{Binding RelativeSource={RelativeSource TemplatedParent}}`. `TemplateBinding`nebo `{RelativeSource TemplatedParent}` použití jsou obě pouze relevantní v jazyce XAML, který definuje šablonu. Další informace najdete v tématu [TemplateBinding – rozšíření značek](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)  
  
 `{RelativeSource FindAncestor}`používá se především ve řízení šablony nebo předvídatelný nezávislý složení uživatelského rozhraní pro případy, kde je vždy očekávána ovládacího prvku ve vizuálním stromu určitého nadřazeného typu. Například může použít položky ovládacího prvku položky `FindAncestor` použití k vytvoření vazby vlastnosti jejich položek řízení nadřazené nadřazený. Nebo můžete použít prvky, které jsou součástí sestavení ovládacího prvku v šabloně `FindAncestor` vazby na nadřazené elementy v této stejné struktury složení.  
  
 V elementu syntaxe objekt `FindAncestor` režimu uvedené v částech syntaxe jazyka XAML, druhý element syntaxe objekt je používán speciálně pro `FindAncestor` režimu. `FindAncestor`režim vyžaduje, aby <xref:System.Windows.Data.RelativeSource.AncestorType%2A> hodnotu. Je nutné nastavit <xref:System.Windows.Data.RelativeSource.AncestorType%2A> jako použití atributu [x: Type – rozšíření značek](../../../../docs/framework/xaml-services/x-type-markup-extension.md) odkaz na typ nadřazené má být vyhledán. <xref:System.Windows.Data.RelativeSource.AncestorType%2A> Hodnota se používá při zpracování požadavku vazba za běhu.  
  
 Pro `FindAncestor` režim, vlastnost volitelné <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> může pomoci odstranit nejednoznačnost předchůdce vyhledávání v případech, kde může být více než jeden předchůdce tohoto typu existující ve stromové struktuře elementu.  
  
 Další informace o tom, jak používat `FindAncestor` režimu, najdete v části <xref:System.Windows.Data.RelativeSource>.  
  
 `{RelativeSource Self}`je užitečné pro scénáře, kde jednu vlastnost instance by měl záviset na hodnotu jiné vlastnosti na stejnou instanci a neexistuje žádný vztah vlastnost obecné závislosti (například převod) již existuje mezi tyto dvě vlastnosti. I když je taková situace vzácná, že existují dvě vlastnosti objektu tak, aby hodnoty oznámena identické (a jsou stejně jako typu), můžete taky použít `Converter` parametru vazby, která má `{RelativeSource Self}`a použijte převaděč pro převod mezi zdrojem a typy cíle. Jiné scénáře `{RelativeSource Self}` je jako součást <xref:System.Windows.MultiDataTrigger>.  
  
 Například následující XAML definuje <xref:System.Windows.Shapes.Rectangle> element takové bez ohledu na to, jaká hodnota zadaná pro <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.Shapes.Rectangle> je vždy čtverce:`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`  
  
 `{RelativeSource PreviousData}`je užitečná v šablonách dat, nebo v případech, kde jsou vazby pomocí kolekce jako zdroj dat. Můžete použít `{RelativeSource PreviousData}` zvýrazněte vztahy mezi přiléhající datových položek v kolekci. Související technika je k vytvoření <xref:System.Windows.Data.MultiBinding> mezi aktuální a předchozí položky zdroj dat a použít převaděč na této vazby k určení rozdílu mezi dvě položky a jejich vlastnosti.  
  
 V následujícím příkladu první <xref:System.Windows.Controls.TextBlock> v položkách šablona zobrazuje aktuální číslo. Druhý <xref:System.Windows.Controls.TextBlock> vazba je <xref:System.Windows.Data.MultiBinding> , jmenovitě má dva <xref:System.Windows.Data.Binding> consistuents: záznam na aktuální záznam a vazbu, která používá úmyslně předchozího záznamu dat pomocí `{RelativeSource PreviousData}`. Potom převaděč na <xref:System.Windows.Data.MultiBinding> vypočítá rozdíl a vrátí ji do vazby.  
  
```xml  
<ListBox Name="fibolist">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <StackPanel Orientation="Horizontal">  
            <TextBlock Text="{Binding}"/>  
            <TextBlock>, difference = </TextBlock>  
                <TextBlock>  
                    <TextBlock.Text>  
                        <MultiBinding Converter="{StaticResource DiffConverter}">  
                            <Binding/>  
                            <Binding RelativeSource="{RelativeSource PreviousData}"/>  
                        </MultiBinding>  
                    </TextBlock.Text>  
                </TextBlock>  
            </StackPanel>  
        </DataTemplate>  
    </ListBox.ItemTemplate>  
```  
  
 Datová vazba popisující, jak koncept neplatí zde najdete v části [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementace XAML procesor je definovaný zpracování pro toto rozšíření značek <xref:System.Windows.Data.RelativeSource> třídy.  
  
 `RelativeSource`je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v XAML použití `{` a `}` znaků v jejich syntaxi atributů, což je konvence, podle kterého XAML procesor rozpozná, že rozšíření značek musí zpracovat atribut. Další informace najdete v tématu [rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Data.Binding>  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Přehled deklarací vazeb](../../../../docs/framework/wpf/data/binding-declarations-overview.md)  
 [x:Type – rozšíření značek](../../../../docs/framework/xaml-services/x-type-markup-extension.md)
