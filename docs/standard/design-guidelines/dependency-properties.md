---
title: Vlastnosti závislosti
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75c83dc75d1c86c89169fcc54220ced2a195bfbe
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079084"
---
# <a name="dependency-properties"></a>Vlastnosti závislosti
Vlastnost závislosti (DP) je regulární vlastnost, která uloží svou hodnotu v úložišti vlastností místo ukládání proměnná typu (pole), např.  
  
 Na vlastnost připojené závislostí je druh vlastnost závislosti nemodelují jako statické metody Get a Set představující "properties" popisující vztahy mezi objekty a jejich kontejnery (například pozici `Button` objektu na `Panel` kontejner).  
  
 **✓ DO** zadejte vlastnosti závislosti, pokud budete potřebovat k podpoře funkce WPF například stylů, aktivační události, vazby dat, animací, dynamické prostředky a dědičnosti vlastností.  
  
## <a name="dependency-property-design"></a>Návrh vlastnosti závislosti  
 **✓ DO** dědí <xref:System.Windows.DependencyObject>, nebo jeden z jeho podtypech při implementaci vlastností závislostí. Typ poskytuje implementaci velmi efektivní úložiště vlastností a automaticky podporuje datové vazby WPF.  
  
 **✓ DO** zadejte regulární vlastnost CLR a veřejné statické jen pro čtení pole ukládání instanci <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> pro každou vlastnost závislosti.  
  
 **✓ DO** implementovat vlastností závislostí voláním metod instance <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> a <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.  
  
 **✓ DO** názvů statické pole vlastnosti závislosti suffixing název vlastnosti s "Vlastnost."  
  
 **X DO NOT** explicitně nastavit výchozí hodnoty vlastností závislostí v kódu; nastavte je v metadatech.  
  
 Pokud nastavíte výchozí vlastnost explicitně, by mohly bránit tuto vlastnost z nastavování některé implicitní prostředky, například styl.  
  
 **X DO NOT** vkládat kód do vlastnosti přistupující objekty než standardní kód pro přístup k statické pole.  
  
 Statické pole, že kód nebude spuštěno Pokud je nastavena implicitní prostředky, například styl, protože práce se styly používá přímo.  
  
 **X DO NOT** zabezpečené data pomocí vlastností závislostí. Vlastnosti závislostí i privátní přístupná veřejně.  
  
## <a name="attached-dependency-property-design"></a>Návrh vlastnosti připojené závislostí  
 Vlastnosti závislostí popsaných v předchozí části představují vnitřní vlastnosti deklarujícího typu; například `Text` vlastností je vlastnost `TextButton`, který deklaruje. Zvláštní druh vlastnost závislosti je vlastnost připojené závislosti.  
  
 Klasické příkladem připojené vlastnosti je <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> vlastnost. Vlastnost představuje pozici sloupce tlačítka (ne mřížky), ale je pouze relevantní tlačítko je součástí do mřížky, takže je "připojeno" k tlačítka pomocí mřížky.  
  
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
  
 Definice připojené vlastnosti vypadá převážně u vlastnosti regulárního závislosti, s tím rozdílem, přístupové objekty jsou reprezentovány statické metody Get a Set:  
  
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
  
## <a name="dependency-property-validation"></a>Ověření vlastností závislostí  
 Vlastnosti často implementovat, co se nazývá ověření. Logiku ověřování provede při pokusu o změnit hodnotu vlastnosti.  
  
 Bohužel přistupující objekty vlastnosti závislost nemůže obsahovat libovolný ověřovací kód. Místo toho logiku ověření závislostí vlastnost je nutné zadat během registrace vlastnost.  
  
 **X DO NOT** chápat logiku ověření pro vlastnost závislosti vlastnosti přistupující objekty. Místo toho předat zpětné volání pro ověření do `DependencyProperty.Register` metody.  
  
## <a name="dependency-property-change-notifications"></a>Oznámení změn vlastností závislosti  
 **X DO NOT** implementovat logiku oznámení změn v přístupové objekty vlastnosti závislosti. Vlastnosti závislosti obsahují integrované změnit funkci oznámení, které musí být použito poskytnutím zpětné volání oznámení změn, aby <xref:System.Windows.PropertyMetadata>.  
  
## <a name="dependency-property-value-coercion"></a>Vynucení hodnotu vlastnosti závislosti  
 Vlastnost převod se provádí při změně hodnoty zadané pro vlastnost setter podle setter předtím, než se skutečně upraví úložiště vlastností.  
  
 **X DO NOT** implementovat logiku na převod přístupové objekty vlastnosti závislosti.  
  
 Vlastnosti závislosti mají integrovanou vynucení funkce a je možné poskytnutím zpětné volání vynucení, aby `PropertyMetadata`.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
- [Obecné vzory návrhu](../../../docs/standard/design-guidelines/common-design-patterns.md)
