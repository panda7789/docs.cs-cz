---
title: Vytvoření klientské aplikace rozhraní .NET Framework (WCF Data Services – rychlý start)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: 86ded7351d435b3a7077f0354d8a923b33a3f2b6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423641"
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a>Vytvoření klientské aplikace rozhraní .NET Framework (WCF Data Services – rychlý start)

Toto je poslední úkol rychlého startu služby WCF Data Services. V této úloze konzolové aplikace do řešení přidat, přidejte odkaz na [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informačního kanálu do této nové klientské aplikace a přístup k datovému kanálu z klientské aplikace pomocí generovaného klienta datové služby třídy a klientské knihovny OData .

> [!NOTE]
> Aplikace klienta na základě rozhraní .NET Framework není vyžadován pro přístup k datový kanál. Datové služby je přístupný součásti žádné aplikace, která využívá datového kanálu OData. Další informace najdete v tématu [použití datové služby v klientské aplikaci](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).

## <a name="to-create-the-client-application-by-using-visual-studio"></a>Vytvoření klientské aplikace pomocí sady Visual Studio

1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na řešení, klikněte na tlačítko **přidat**a potom klikněte na tlačítko **nový projekt**.

2.  V levém podokně vyberte **nainstalováno** > [**Visual C#** nebo **jazyka Visual Basic**] > **Windows Desktop**a pak vyberte **Aplikace WPF** šablony.

3.  Zadejte `NorthwindClient` pro název projektu a pak klikněte na tlačítko **OK**.

4.  Otevřete soubor MainWindow.xaml a nahraďte kód XAML následujícím kódem:

     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml#window1xaml)]

## <a name="to-add-a-data-service-reference-to-the-project"></a>Chcete-li přidat odkaz na službu do projektu

1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt NorthwindClient, klikněte na tlačítko **přidat** > **odkaz na službu**a potom klikněte na tlačítko **zjišťování** .

     Zobrazí se datová služba Northwind, kterou jste vytvořili v prvním úkolem.

2.  V **Namespace** textového pole, typ `Northwind`a potom klikněte na tlačítko **OK**.

     To přidá nový soubor kódu do projektu, který obsahuje data třídy, které se používají pro přístup k interakci s prostředky služby dat jako objektů. Datové třídy jsou vytvořené v oboru názvů `NorthwindClient.Northwind`.

## <a name="to-access-data-service-data-in-the-wpf-application"></a>Pro přístup k datům služby dat v aplikaci WPF

1.  V **Průzkumníka řešení** pod **NorthwindClient**, klikněte pravým tlačítkem na projekt a klikněte na tlačítko **přidat odkaz**.

2.  V **přidat odkaz** dialogové okno, klikněte na tlačítko **.NET** kartu, vyberte knihovně System.Data.Services.Client.dll sestavení a pak klikněte na tlačítko **OK**.

3. V **Průzkumníka řešení** pod **NorthwindClient**, otevřete stránku kódem pro souboru MainWindow.xaml a přidejte následující `using` – příkaz (`Imports` v jazyce Visual Basic).

     [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#using)]
     [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#using)]

3.  Vložte následující kód, který se dotazuje služby data a vytvoří výsledek, který má vazbu <xref:System.Data.Services.Client.DataServiceCollection%601> do `MainWindow` třídy:

    > [!NOTE]
    > Je třeba nahradit název hostitele `localhost:12345` serveru a port, který je hostitelem vaší instance datová služba Northwind.

     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#querycode)]

4.  Vložte následující kód, který ukládá změny do `MainWindow` třídy:

     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#savechanges)]

## <a name="to-build-and-run-the-northwindclient-application"></a>Sestavte a spusťte aplikaci NorthwindClient

1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt NorthwindClient a vyberte **nastavit jako spouštěný projekt**.

2.  Stisknutím klávesy **F5** ke spuštění aplikace.

     Tím se sestaví řešení a spustí klientské aplikace. Data se požadované služby a zobrazovat v konzole.

3.  Úprava hodnoty v **množství** sloupců datové mřížce a potom klikněte na **Uložit**.

     Změny se uloží do datové služby.

    > [!NOTE]
    > Tato verze aplikace NorthwindClient nepodporuje přidávání a odstraňování entit.

## <a name="next-steps"></a>Další kroky

Úspěšně jste vytvořili klientská aplikace, který přistupuje k ukázkového datového kanálu OData s názvem Northwind. Také jste dokončili rychlé spuštění služeb WCF Data Services!

Další informace o přístupu k OData informačního kanálu ze [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikace, najdete v článku [klientské knihovny WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).

## <a name="see-also"></a>Viz také

- [Začínáme](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
- [Prostředky](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)
