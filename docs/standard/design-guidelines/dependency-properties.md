---
title: Vlastnosti závislosti
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: bd12d05dbba133503778e6df3cd0e6c3e5689d5b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709488"
---
# <a name="dependency-properties"></a>Vlastnosti závislosti
Vlastnost závislosti (DP) je obvyklá vlastnost, která ukládá její hodnotu do úložiště vlastností místo jejich uložení do proměnné typu (pole), například.  
  
 Připojená vlastnost Dependency je druh vlastnosti závislosti, která se modeluje jako statické metody Get a set, které představují vlastnosti popisující vztahy mezi objekty a jejich kontejnery (například umístění objektu `Button` v kontejneru `Panel`).  
  
 **✓ DO** zadejte vlastnosti závislosti, pokud budete potřebovat k podpoře funkce WPF například stylů, aktivační události, vazby dat, animací, dynamické prostředky a dědičnosti vlastností.  
  
## <a name="dependency-property-design"></a>Návrh vlastnosti závislosti  
 **✓ DO** dědí <xref:System.Windows.DependencyObject>, nebo jeden z jeho podtypech při implementaci vlastností závislostí. Typ poskytuje velmi efektivní implementaci úložiště vlastností a automaticky podporuje datovou vazbu WPF.  
  
 **✓ DO** zadejte regulární vlastnost CLR a veřejné statické jen pro čtení pole ukládání instanci <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> pro každou vlastnost závislosti.  
  
 **✓ DO** implementovat vlastností závislostí voláním metod instance <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> a <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.  
  
 **✓ DO** názvů statické pole vlastnosti závislosti suffixing název vlastnosti s "Vlastnost."  
  
 **X DO NOT** explicitně nastavit výchozí hodnoty vlastností závislostí v kódu; nastavte je v metadatech.  
  
 Pokud nastavíte výchozí nastavení vlastnosti explicitně, můžete zabránit tomu, aby se tato vlastnost nastavila některými implicitními prostředky, jako je styl.  
  
 **X DO NOT** vkládat kód do vlastnosti přistupující objekty než standardní kód pro přístup k statické pole.  
  
 Tento kód nebude proveden, pokud je vlastnost nastavena pomocí implicitních prostředků, jako je například styl, protože styl používá přímo pole static.  
  
 **X DO NOT** zabezpečené data pomocí vlastností závislostí. K vlastnostem soukromé závislosti lze přistupovat i na veřejném.  
  
## <a name="attached-dependency-property-design"></a>Návrh vlastnosti připojené závislosti  
 Vlastnosti závislosti popsané v předchozí části označují vnitřní vlastnosti deklarovaného typu; například vlastnost `Text` je vlastnost `TextButton`, která ji deklaruje. Speciálním druhem vlastnosti závislosti je vlastnost připojené závislosti.  
  
 Klasickým příkladem připojené vlastnosti je vlastnost <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>. Vlastnost představuje pozici sloupce tlačítko (ne mřížka), ale je relevantní pouze v případě, že je tlačítko obsaženo v mřížce, a proto je "připojené" k tlačítkům na základě mřížky.  
  
```xaml
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
  
    <Button Grid.Column="0">Click</Button>  
    <Button Grid.Column="1">Clack</Button>  
</Grid>  
```  
  
 Definice připojené vlastnosti vypadá hlavně podobně jako vlastnost běžné závislosti s tím rozdílem, že přistupující objekty jsou reprezentovány pomocí statických metod get a set:  
  
```csharp
public class Grid {  
  
    public static int GetColumn(DependencyObject obj) {  
        return (int)obj.GetValue(ColumnProperty);  
    }  
  
    public static void SetColumn(DependencyObject obj, int value) {  
        obj.SetValue(ColumnProperty,value);  
    }  
  
    public static readonly DependencyProperty ColumnProperty =  
        DependencyProperty.RegisterAttached(  
            "Column",  
            typeof(int),  
            typeof(Grid)  
    );  
}  
```  
  
## <a name="dependency-property-validation"></a>Ověřování vlastností závislosti  
 Vlastnosti často implementují, co se nazývá ověřování. Logika ověřování se spustí, když se provede pokus o změnu hodnoty vlastnosti.  
  
 Přístupové objekty vlastnosti bohužel nemůžou obsahovat libovolný ověřovací kód. Místo toho je nutné při registraci vlastnosti zadat logiku ověřování vlastností závislostí.  
  
 **X DO NOT** chápat logiku ověření pro vlastnost závislosti vlastnosti přistupující objekty. Místo toho předejte zpětné volání ověření do metody `DependencyProperty.Register`.  
  
## <a name="dependency-property-change-notifications"></a>Oznámení o změně vlastnosti závislosti  
 **X DO NOT** implementovat logiku oznámení změn v přístupové objekty vlastnosti závislosti. Vlastnosti závislosti mají vestavěnou funkci oznámení změn, kterou je nutné použít k poskytnutí zpětného volání oznámení o změně <xref:System.Windows.PropertyMetadata>.  
  
## <a name="dependency-property-value-coercion"></a>Hodnota vlastnosti závislosti – vynucení  
 K převodu vlastnosti dojde, pokud je hodnota zadaná metodě setter vlastnosti změněna před samotným úpravou úložiště vlastností.  
  
 **X DO NOT** implementovat logiku na převod přístupové objekty vlastnosti závislosti.  
  
 Vlastnosti závislosti mají integrovanou funkci vynucení a lze ji použít poskytnutím zpětného volání pro `PropertyMetadata`.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Obecné vzory návrhu](../../../docs/standard/design-guidelines/common-design-patterns.md)
