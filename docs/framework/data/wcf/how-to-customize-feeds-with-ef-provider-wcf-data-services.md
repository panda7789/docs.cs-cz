---
title: 'Postupy: Přizpůsobení informačních kanálů prostřednictvím zprostředkovatele Entity Framework (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: fd16272e-36f2-415e-850e-8a81f2b17525
ms.openlocfilehash: 9770527f41b4981e63d65f27c409b2ce5583d2cc
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517210"
---
# <a name="how-to-customize-feeds-with-the-entity-framework-provider-wcf-data-services"></a>Postupy: Přizpůsobení informačních kanálů prostřednictvím zprostředkovatele Entity Framework (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umožňuje přizpůsobit Atom serializaci v odpovědi služby data tak, aby vlastnosti entity mohou být namapovány na nepoužívané prvky, které jsou definovány v AtomPub protokolu. Toto téma ukazuje, jak definovat atributů mapování pro typy entity v datovém modelu, který je definován v souboru .edmx s použitím poskytovateli rozhraní Entity Framework. Další informace najdete v tématu [přizpůsobení informačního kanálu](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
 V tomto tématu se ručně upravit soubor .edmx vygeneruje nástroj, který obsahuje datový model. Musíte ručně upravit soubor, protože rozšíření do datového modelu nejsou podporovány v návrháři entit. Další informace o souboru EDMX, které generují nástroje modelu Entity Data Model najdete v tématu [edmx soubor přehled (Entity Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)). V příkladu v tomto tématu se používá Northwind ukázková data service a automaticky vygenerovaných tříd klientské datové služby. Tuto službu a třídy dat klientů jsou vytvořeny po dokončení [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-manually-modify-the-northwindedmx-file-to-add-feed-customization-attributes"></a>Jak ručně upravit soubor Northwind.edmx přidat atributy přizpůsobení informačního kanálu  
  
1. V **Průzkumníku řešení**, klikněte pravým tlačítkem myši `Northwind.edmx` souboru a pak klikněte na **otevřít v programu**.  
  
2. V **otevřít v programu-Northwind.edmx** dialogu **editoru XML**a potom klikněte na tlačítko **OK**.  
  
3. Vyhledejte `ConceptualModels` prvku a nahraďte existující `Customers` typ entity s následující element, který obsahuje kanálu přizpůsobení mapování atributů:  
  
     [!code-xml[Astoria Custom Feeds#EdmFeedCustomers](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/northwind.csdl#edmfeedcustomers)]  
  
4. Uložte změny a zavřete soubor Northwind.edmx.  
  
5. (Volitelné) Klikněte pravým tlačítkem na soubor Northwind.edmx a potom klikněte na tlačítko **spustit vlastní nástroj**.  
  
     To obnoví souboru vrstvy objektu, který může být nutné.  
  
6. Znovu zkompilujte projekt.  
  
## <a name="example"></a>Příklad  
 V předchozím příkladu vrátí následující výsledek pro identifikátor URI `http://myservice/Northwind.svc/Customers('ALFKI')`.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/edmfeedresult.xml#edmfeedresult)]  
  
## <a name="see-also"></a>Viz také:

- [Zprostředkovatel Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)
