---
title: "Vytvoření aplikace klienta rozhraní .NET Framework (rychlý start WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 563d08a5907c8248a74ba992de17ac3dd0679827
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a>Vytvoření aplikace klienta rozhraní .NET Framework (rychlý start WCF Data Services)
Toto je poslední úlohy [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] rychlý start. V této úloze bude konzolovou aplikaci do řešení přidat, přidejte odkaz na [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] kanálu na tuto novou klientskou aplikaci a přístup [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu z klientské aplikace pomocí generovaného klienta datových služba tříd a klienta knihovny.  
  
> [!NOTE]
>  Aplikace založené na rozhraní .NET Framework klienta není potřeba přístup k datovému kanálu. Služba data budou mít přístup všechny součásti aplikace, který využívá [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu. Další informace najdete v tématu [pomocí datové služby v aplikaci klienta](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).  
  
### <a name="to-create-the-client-application-by-using-visual-studio"></a>Chcete-li vytvořit klientskou aplikaci pomocí sady Visual Studio  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na řešení, klikněte na **přidat**a potom klikněte na **nový projekt**.  
  
2.  V **typy projektů**, klikněte na tlačítko **Windows**a potom vyberte **aplikaci WPF** v **šablony** podokně.  
  
3.  Zadejte `NorthwindClient` název projektu a pak klikněte na tlačítko **OK**.  
  
4.  Otevřete soubor MainWindow.xaml a nahraďte kód XAML následujícím kódem:  
  
     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml#window1xaml)]  
  
### <a name="to-add-a-data-service-reference-to-the-project"></a>Chcete-li přidat odkaz na službu do projektu  
  
1.  Klikněte pravým tlačítkem na projekt NorthwindClient, klikněte na tlačítko **přidat odkaz na službu**a potom klikněte na **Discover**.  
  
     Zobrazí se služba Northwind dat, který jste vytvořili v první úloze.  
  
2.  V **Namespace** textového pole, typ `Northwind`a potom klikněte na **OK**.  
  
     To přidá nový soubor kódu do projektu, který obsahuje datové třídy, které se používají pro přístup a pracovat s prostředky služby data jako objekty. Datových tříd, které jsou vytvořené v oboru názvů `NorthwindClient.Northwind`.  
  
### <a name="to-access-data-service-data-in-the-wpf-application"></a>Pro přístup k datům služby dat v aplikaci WPF  
  
1.  V **Průzkumníku řešení** pod **NorthwindClient**, klikněte pravým tlačítkem na projekt a klikněte na **přidat odkaz na**.  
  
2.  V dialogovém okně Přidat odkaz klepněte **.NET** vyberte knihovně System.Data.Services.Client.dll sestavení a pak klikněte na tlačítko **OK**. V **Průzkumníku řešení** pod **NorthwindClient**, otevřete stránku kód pro soubor MainWindow.xaml a přidejte následující `using` – příkaz (`Imports` v jazyce Visual Basic).  
  
     [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#using)]
     [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#using)]  
  
3.  Vložte následující kód, který se dotazuje služby dat a sváže výsledek, který má <xref:System.Data.Services.Client.DataServiceCollection%601> do `MainWindow` třídy:  
  
    > [!NOTE]
    >  Je třeba nahradit název hostitele `localhost:12345` se serverem a port, který je hostitelem vaší instance služby data Northwind.  
  
     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#querycode)]  
  
4.  Vložte následující kód, který uloží změny do `MainWindow` třídy:  
  
     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#savechanges)]  
  
### <a name="to-build-and-run-the-northwindclient-application"></a>Sestavení a spuštění aplikace NorthwindClient  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt NorthwindClient a vyberte **nastavit jako spouštěný projekt**.  
  
2.  Stisknutím klávesy F5 a spusťte aplikaci.  
  
     Tím se vytvoří řešení a spustí klientské aplikace. Data jsou požadovaná ze služby a zobrazovat v konzole.  
  
3.  Úprava hodnoty v **množství** sloupce mřížky dat a pak klikněte na **Uložit**.  
  
     Změny budou uloženy ve službě data.  
  
    > [!NOTE]
    >  Tato verze aplikace NorthwindClient nepodporuje přidávání a odstraňování entit.  
  
## <a name="next-steps"></a>Další kroky  
 Úspěšně jste vytvořili aplikace klienta, která přistupuje k ukázce Northwind [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu. Když jste dokončili [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] rychlý start. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]přístup [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikace, najdete v části [WCF Data Services klientské knihovny](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).  
  
## <a name="see-also"></a>Viz také  
 [Začínáme](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [Prostředky](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)
