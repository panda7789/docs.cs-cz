---
title: "Postupy: přizpůsobení informačních kanálů v aplikaci zprostředkovatele Entity Framework (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: fd16272e-36f2-415e-850e-8a81f2b17525
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72c26f6c86187579bc8af4dde034cba30fb6a90b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-feeds-with-the-entity-framework-provider-wcf-data-services"></a>Postupy: přizpůsobení informačních kanálů v aplikaci zprostředkovatele Entity Framework (služby WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Umožňuje přizpůsobit Atom serializaci v odpovědi data služby tak, aby vlastnosti entity, může být namapovaný na nepoužívané elementy, které jsou definovány v AtomPub protokolu. Toto téma ukazuje, jak definovat mapování atributů pro typy entit v datovém modelu, který je definován v souboru EDMX pomocí zprostředkovatele Entity Framework. Další informace najdete v tématu [kanálu přizpůsobení](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
 V tomto tématu ručně upravíte soubor EDMX generované nástroj, který obsahuje datový model. Soubor musí ručně upravit, protože rozšíření do datového modelu Entity Designer nepodporuje. Další informace o souboru .edmx, který nástroje modelu Entity Data Model vytvořit najdete v tématu [.edmx souboru přehled](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4). V příkladu v tomto tématu používá Northwind ukázková data služby a automaticky generovaný klienta dat služby třídy. Tato služba a datové třídy klienta se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-manually-modify-the-northwindedmx-file-to-add-feed-customization-attributes"></a>Pro ruční úpravy souboru Northwind.edmx přidejte informačního kanálu vlastní atributy  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši `Northwind.edmx` souboru a potom klikněte na **Otevřít protokolem**.  
  
2.  V **otevřít v programu - Northwind.edmx** dialogové okno, vyberte **editoru XML**a potom klikněte na **OK**.  
  
3.  Vyhledejte `ConceptualModels` elementu a nahradit stávající `Customers` typ entity s následující element, který obsahuje kanálu atributy mapování přizpůsobení:  
  
     [!code-xml[Astoria Custom Feeds#EdmFeedCustomers](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/northwind.csdl#edmfeedcustomers)]  
  
4.  Uložte změny a zavřete soubor Northwind.edmx.  
  
5.  (Volitelné) Klikněte pravým tlačítkem na soubor Northwind.edmx a pak klikněte na **spustit nástroj pro vlastní**.  
  
     To regeneruje souboru vrstvy objektu, který může být nutný.  
  
6.  Znovu zkompiluje projektu.  
  
## <a name="example"></a>Příklad  
 Předchozí příklad vrátí následující výsledek pro identifikátor URI `http://myservice/``Northwind.svc/Customers('ALFKI')`.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/edmfeedresult.xml#edmfeedresult)]  
  
## <a name="see-also"></a>Viz také  
 [Zprostředkovatel Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)
