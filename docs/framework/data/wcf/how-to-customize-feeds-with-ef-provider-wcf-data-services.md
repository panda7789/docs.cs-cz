---
title: 'Postupy: Přizpůsobení informačních kanálů pomocí poskytovatele Entity Framework (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: fd16272e-36f2-415e-850e-8a81f2b17525
ms.openlocfilehash: 8f994065ea42d6fc522fa297cafa8c46a8164e67
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780148"
---
# <a name="how-to-customize-feeds-with-the-entity-framework-provider-wcf-data-services"></a>Postupy: Přizpůsobení informačních kanálů pomocí poskytovatele Entity Framework (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umožňuje přizpůsobit serializaci Atom v odpovědi na datovou službu, takže vlastnosti entity mohou být namapovány na nepoužívané prvky, které jsou definovány v protokolu AtomPub. Toto téma ukazuje, jak definovat atributy mapování pro typy entit v datovém modelu, který je definován v souboru. edmx pomocí poskytovatele Entity Framework. Další informace najdete v tématu [přizpůsobení informačního kanálu](feed-customization-wcf-data-services.md).  
  
 V tomto tématu ručně upravíte soubor. edmx generovaný nástrojem, který obsahuje datový model. Soubor je nutné ručně upravit, protože rozšíření pro datový model nejsou podporována Entity Designer. Další informace o souboru. edmx, který generují nástroje model EDM (Entity Data Model), najdete v tématu [Přehled souborů. edmx (Entity Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)). V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
### <a name="to-manually-modify-the-northwindedmx-file-to-add-feed-customization-attributes"></a>Ruční úprava souboru Northwind. edmx pro přidání atributů přizpůsobení informačního kanálu  
  
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši `Northwind.edmx` na soubor a potom klikněte na možnost **otevřít v programu**.  
  
2. V dialogovém okně **otevřít v aplikaci-Northwind. edmx** vyberte **Editor XML**a pak klikněte na **OK**.  
  
3. Vyhledejte prvek a nahraďte existující `Customers` typ entity následujícím prvkem, který obsahuje atributy mapování přizpůsobení kanálu: `ConceptualModels`  
  
     [!code-xml[Astoria Custom Feeds#EdmFeedCustomers](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/northwind.csdl#edmfeedcustomers)]  
  
4. Uložte změny a zavřete soubor Northwind. edmx.  
  
5. Volitelné Klikněte pravým tlačítkem na soubor Northwind. edmx a pak klikněte na **Spustit vlastní nástroj**.  
  
     Tím se znovu vygeneruje soubor vrstvy objektu, který může být povinný.  
  
6. Zkompilujte projekt znovu.  
  
## <a name="example"></a>Příklad  
 Předchozí příklad vrátí následující výsledek pro identifikátor URI `http://myservice/Northwind.svc/Customers('ALFKI')`.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/edmfeedresult.xml#edmfeedresult)]  
  
## <a name="see-also"></a>Viz také:

- [Zprostředkovatel Entity Framework](entity-framework-provider-wcf-data-services.md)
