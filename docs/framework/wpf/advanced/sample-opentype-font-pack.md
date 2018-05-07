---
title: Ukázková sada písem OpenType
ms.date: 03/30/2017
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
ms.openlocfilehash: bec890f7937965c314ccf16b4142905c52ceff49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="sample-opentype-font-pack"></a>Ukázková sada písem OpenType
Toto téma obsahuje přehled vzorku [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma, která jsou distribuované s [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)]. Podporu je víc písem. ukázka rozšířené [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] funkce, které mohou být využívána [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace.  
  
  
<a name="overview"></a>   
## <a name="fonts-in-the-opentype-font-pack"></a>V sadě písem OpenType písem.  
 [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] Poskytuje sadu ukázka [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma, která můžete použít při vytváření [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikací. Ukázka písem se zadávají v rámci licence od horní dotah Corporation. Tato písma implementovat pouze podmnožinu celkový počet funkcí, které jsou definované [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] formátu. Následující tabulka uvádí názvy vzorku [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písem.  
  
|**Jméno**|**Soubor**|  
|--------------|--------------|  
|Kootenay|Kooten.ttf|  
|Lindsey|Linds.ttf|  
|Miramonte|Miramo.ttf|  
|Miramonte tučně|Miramob.ttf|  
|Pericles|Peric.ttf|  
|Lehký Pericles|Pericl.ttf|  
|Pescadero|Pesca.ttf|  
|Pescadero tučně|Pescab.ttf|  
  
 Následující obrázek ukazuje, jaké vzorku [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] vypadat písem.  
  
 ![Seznam názvů písem v ukázkové sadě písem](../../../../docs/framework/wpf/advanced/media/samplefontpack01.gif "samplefontpack01")  
V sadě písem OpenType písem.  
  
 Ukázka písem se zadávají v rámci licence od horní dotah Corporation. Horní dotah je zprostředkovatel produktů pokročilé písma. Licence rozšířené nebo vlastní verzích ukázka písem, najdete v tématu [horní dotah Corporation webu](http://go.microsoft.com/fwlink/?LinkId=182627).  
  
> [!NOTE]
>  Jako vývojář je vaší povinností ujistit, že máte požadovanou licenci práva pro libovolného písma vložení v aplikaci nebo v opačném případě znovu distribuovat.  
  
<a name="installing_the_fonts"></a>   
## <a name="installing-the-fonts"></a>Instalace písma  
 Máte možnost instalace vzorku [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písem na výchozí hodnoty [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] písem directory **\WINDOWS\Fonts**. Použijte ovládací panel písma pro instalaci písem. Jakmile jsou tyto písem v počítači, které jsou přístupné na všechny aplikace, které odkazují na výchozí [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] písem. Můžete zobrazit reprezentativní sadu znaků v několika velikostí písma zvýší – klikněte na soubor písma. Následující snímek obrazovky ukazuje soubor písma Lindsey Linds.ttf.  
  
 ![Písmo Lindsey &#40;OpenType&#41;](../../../../docs/framework/wpf/advanced/media/typographyinwpf-04.png "TypographyInWPF_04")  
Zobrazení Písmo Lindsey  
  
<a name="using_the_fonts"></a>   
## <a name="using-the-fonts"></a>Použití písem  
 Existují dva způsoby, které můžete písem v aplikaci. Písma můžete přidat do vaší aplikace jako obsahu položky, které nejsou vloženy jako prostředky v rámci sestavení projektu. Alternativně můžete přidat písem do vaší aplikace jako položky projektu prostředků, které jsou vloženy do souborů sestavení aplikace. Další informace najdete v tématu [balení písma s aplikacemi](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Documents.Typography>  
 [Funkce písma OpenType](../../../../docs/framework/wpf/advanced/opentype-font-features.md)  
 [Balení písem s aplikacemi](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)
