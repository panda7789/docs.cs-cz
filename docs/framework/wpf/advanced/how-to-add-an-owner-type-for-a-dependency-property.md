---
title: 'Postupy: Přidání typu vlastníka pro vlastnost závislosti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
ms.openlocfilehash: 5ddc85d159b4bf81751428c13c234c5e53be8ad4
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401131"
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a>Postupy: Přidání typu vlastníka pro vlastnost závislosti
Tento příklad ukazuje, jak přidat třídu jako vlastníka vlastnosti závislosti registrované pro jiný typ. Tímto způsobem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dokáže čtenář a systém vlastností rozpoznat třídu jako dalšího vlastníka vlastnosti. Přidání jako vlastníka můžete volitelně povolit přidání třídy pro zadání metadat specifických pro typ.  
  
 V následujícím příkladu `StateProperty` je vlastnost zaregistrována `MyStateControl` třídou. Třída `UnrelatedStateControl` přidá sebe samu jako vlastníka `StateProperty` pomocí <xref:System.Windows.DependencyProperty.AddOwner%2A> metody, konkrétně pomocí signatury, která umožňuje nová metadata pro vlastnost závislosti, protože existuje v přidávaném typu. Všimněte si, že byste měli poskytnout přístupové objekty modulu CLR (Common Language Runtime) pro vlastnost podobně jako v příkladu, který je uveden v příkladu [implementace vlastnosti závislosti](how-to-implement-a-dependency-property.md) , a také znovu vystavit identifikátor vlastnosti závislosti pro třídu, která je přidávána jako vlastník.  
  
 Bez obálky může vlastnost Dependency i nadále pracovat z perspektivy programového přístupu pomocí <xref:System.Windows.DependencyObject.GetValue%2A> nebo. <xref:System.Windows.DependencyObject.SetValue%2A> Ale obvykle chcete, aby toto chování systému vlastností bylo paralelně paralelní s obálkami vlastností CLR. Obálky usnadňují nastavení vlastnosti závislosti programově a umožňují nastavit vlastnosti jako [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atributy.  
  
 Chcete-li zjistit, jak přepsat výchozí metadata, přečtěte si téma [přepis metadat pro vlastnost závislosti](how-to-override-metadata-for-a-dependency-property.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a>Viz také:

- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
- [Přehled vlastností závislosti](dependency-properties-overview.md)
