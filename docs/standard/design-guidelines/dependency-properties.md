---
title: "Vlastnosti závislosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 21e2026e7ce0f2dcf1ffc9a328b1bb9630cd8fbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="dependency-properties"></a>Vlastnosti závislosti
Vlastnost závislosti (DP) je regulární vlastnost, která ukládá v úložišti vlastnost místo ukládání typ proměnné (pole), například jeho hodnotu.  
  
 Ve vlastnosti připojené závislostí je druh vlastnost závislosti, které jsou modelovat jako statické metody Get a sady reprezentující "vlastnosti" popisující vztahy mezi objekty a jejich kontejnery (například pozici `Button` objekt v `Panel` kontejner).  
  
 **PROVEĎTE ✓** zadejte vlastnosti závislosti, pokud budete potřebovat k podpoře funkce WPF například stylů, aktivační události, vazby dat, animací, dynamické prostředky a dědičnosti vlastností.  
  
## <a name="dependency-property-design"></a>Návrh vlastnost závislosti  
 **PROVEĎTE ✓** dědí <xref:System.Windows.DependencyObject>, nebo jeden z jeho podtypech při implementaci vlastností závislostí. Typ poskytuje velmi efektivní implementaci úložiště vlastností a automaticky podporuje datové vazby WPF.  
  
 **PROVEĎTE ✓** zadejte regulární vlastnost CLR a veřejné statické jen pro čtení pole ukládání instanci <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> pro každou vlastnost závislosti.  
  
 **PROVEĎTE ✓** implementovat vlastností závislostí voláním metod instance <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> a <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.  
  
 **PROVEĎTE ✓** názvů statické pole vlastnosti závislosti suffixing název vlastnosti s "Vlastnost."  
  
 **X nesmí** explicitně nastavit výchozí hodnoty vlastností závislostí v kódu; nastavte je v metadatech.  
  
 Pokud nastavíte výchozí vlastnost explicitně, vám může zabránit tuto vlastnost se nastavuje některé implicitní prostředky, jako je například stylů.  
  
 **X nesmí** vkládat kód do vlastnosti přistupující objekty než standardní kód pro přístup k statické pole.  
  
 Statické pole, kód nebude spustit, pokud je vlastnost nastavena implicitní prostředky, jako je například stylů, protože styly používá přímo.  
  
 **X nesmí** zabezpečené data pomocí vlastností závislostí. Veřejně přístupná vlastností i privátní závislostí.  
  
## <a name="attached-dependency-property-design"></a>Návrh vlastnost připojené závislostí  
 Závislost vlastností popsaných v předchozí části představují vnitřní vlastnosti deklarující typ; například `Text` vlastnost je vlastností `TextButton`, který deklaruje ho. Zvláštní druh vlastnost závislosti je vlastnost připojené závislosti.  
  
 Je classic třeba přidružená vlastnost <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> vlastnost. Vlastnost představuje pozici sloupce tlačítka (ne mřížky), ale je pouze relevantní Pokud tlačítko je obsažen v mřížce, a tudíž je "připojen" na tlačítka podle mřížky.  
  
```  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
  
    <Button Grid.Column="0">Click</Button>  
    <Button Grid.Column="1">Clack</Button>  
</Grid>  
```  
  
 Definice přidružená vlastnost vypadá nejčastěji, vlastnosti regulární závislosti, s tím rozdílem, že přístupové objekty jsou reprezentované pomocí statické metody Get a sady:  
  
```  
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
 Vlastnosti často implementovat, co se nazývá ověření. Logiku ověření provede, když je proveden pokus o ke změně hodnoty vlastnosti.  
  
 Přístupové objekty vlastnosti závislosti bohužel nemůže obsahovat libovolný ověřovacího kódu. Místo toho je třeba zadat během registrace vlastnost logiku ověření pro vlastnost závislosti.  
  
 **X nesmí** chápat logiku ověření pro vlastnost závislosti vlastnosti přistupující objekty. Místo toho předat zpětné volání pro ověření do `DependencyProperty.Register` metoda.  
  
## <a name="dependency-property-change-notifications"></a>Oznámení o změnách závislostí vlastnost  
 **X nesmí** implementovat logiku oznámení změn v přístupové objekty vlastnosti závislosti. Vlastnosti závislosti mají funkce oznámení předdefinované změnu, která použije zadáním zpětné volání oznámení změny na <xref:System.Windows.PropertyMetadata>.  
  
## <a name="dependency-property-value-coercion"></a>Převod hodnotu vlastnosti závislosti  
 Vlastnost převod probíhá při hodnotě zadané pro vlastnost setter je upraveném nastavovací metoda předtím, než je ve skutečnosti Změna úložiště vlastnost.  
  
 **X nesmí** implementovat logiku na převod přístupové objekty vlastnosti závislosti.  
  
 Vlastností závislostí obsahují předdefinované převod funkci a použitím zadáním zpětné volání pro převod `PropertyMetadata`.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny pro návrh Framework](../../../docs/standard/design-guidelines/index.md)  
 [Obecné vzory návrhu](../../../docs/standard/design-guidelines/common-design-patterns.md)
