---
title: 'Postupy: přizpůsobení informačních kanálů pomocí poskytovatele Entity Framework (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: fd16272e-36f2-415e-850e-8a81f2b17525
ms.openlocfilehash: 16c3741068d19fb55d8acfd28e4f83df633b0b09
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569157"
---
# <a name="how-to-customize-feeds-with-the-entity-framework-provider-wcf-data-services"></a>Postupy: přizpůsobení informačních kanálů pomocí poskytovatele Entity Framework (WCF Data Services)
WCF Data Services umožňuje přizpůsobit serializaci Atom v odpovědi na datovou službu, takže vlastnosti entity mohou být namapovány na nepoužívané prvky, které jsou definovány v protokolu AtomPub. Toto téma ukazuje, jak definovat atributy mapování pro typy entit v datovém modelu, který je definován v souboru. edmx pomocí poskytovatele Entity Framework. Další informace najdete v tématu [přizpůsobení informačního kanálu](feed-customization-wcf-data-services.md).  
  
 V tomto tématu ručně upravíte soubor. edmx generovaný nástrojem, který obsahuje datový model. Soubor je nutné ručně upravit, protože rozšíření pro datový model nejsou podporována Entity Designer. Další informace o souboru. edmx, který generují nástroje model EDM (Entity Data Model), najdete v tématu [Přehled souborů. edmx (Entity Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)). V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
### <a name="to-manually-modify-the-northwindedmx-file-to-add-feed-customization-attributes"></a>Ruční úprava souboru Northwind. edmx pro přidání atributů přizpůsobení informačního kanálu  
  
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor `Northwind.edmx` a pak klikněte na možnost **otevřít v programu**.  
  
2. V dialogovém okně **otevřít v aplikaci-Northwind. edmx** vyberte **Editor XML**a pak klikněte na **OK**.  
  
3. Vyhledejte prvek `ConceptualModels` a nahraďte existující typ entity `Customers` následujícím prvkem, který obsahuje atributy mapování přizpůsobení kanálu:  
  
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
