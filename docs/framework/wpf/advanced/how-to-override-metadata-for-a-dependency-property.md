---
title: 'Postupy: Přetížení metadat pro vlastnost závislosti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [WPF], overriding for dependency properties
- dependency properties [WPF], overriding metadata for
- overriding metadata for dependency properties [WPF]
ms.assetid: f90f026e-60d8-428a-933d-edf0dba4441f
ms.openlocfilehash: ba2f98d262f5c43dbd0c07d356556cdc3ec4b8dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589750"
---
# <a name="how-to-override-metadata-for-a-dependency-property"></a>Postupy: Přetížení metadat pro vlastnost závislosti
Tento příklad ukazuje, jak přepsat výchozí závislost vlastnost metadat, který přichází z děděné třídy, voláním <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> metoda a poskytuje metadata pro konkrétní typ.  
  
## <a name="example"></a>Příklad  
 Definováním jeho <xref:System.Windows.PropertyMetadata>, třídy můžete definovat vlastnosti závislosti chování, například jeho výchozí hodnotu a vlastnost systému zpětná volání. Mnoho závislostí vlastnosti třídy již máte výchozí metadat vytvořeno jako součást procesu registrace. To zahrnuje vlastnosti závislosti, které jsou součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]. Třídu, která dědí vlastnost závislosti prostřednictvím jeho dědičnosti třídy můžete přepsat původní metadata, aby souhlasila charakteristiky vlastnost, která lze změnit prostřednictvím metadat se žádné požadavky na konkrétní podtřídy.  
  
 Přepsání metadat pro vlastnost závislosti je nutné provést před tuto vlastnost umístěných používá vlastnost systému (to odpovídá na dobu, která jsou vytvořena instance určité instance objektů, které registrují vlastnost). Volání <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> se musí provádět v rámci typu, který se poskytuje samostatně jako statické konstruktory `forType` parametr <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>. Pokud se pokusíte změnit metadat existuje instancí typu vlastníka, to nebudou vyvolávat výjimky, ale bude způsobit nekonzistentní chování v systému vlastností. Navíc metadat lze pouze přepsat jednou podle typu. Následné pokusy pro přepis metadat na stejný typ bude vyvolána výjimka.  
  
 V následujícím příkladu, vlastní třídu `MyAdvancedStateControl` přepisuje metadata stanovené `StateProperty` podle `MyAdvancedStateControl` s novými metadaty vlastnost. Například výchozí hodnota `StateProperty` je nyní `true` když je dotazován vlastnost na nově vytvořený `MyAdvancedStateControl` instance.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#myadvancedstatecontrol)]
[!code-vb[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#myadvancedstatecontrol)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.DependencyProperty>
- [Přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [Vlastní vlastnosti závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
- [Témata s postupy](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
