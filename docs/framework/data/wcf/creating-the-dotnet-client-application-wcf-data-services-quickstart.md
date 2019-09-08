---
title: Vytvoření klientské aplikace .NET Framework (WCF Data Services rychlý Start)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: 9995a509bf997298d991a1f66cfdf3cae6cd0395
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790965"
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a>Vytvoření klientské aplikace .NET Framework (WCF Data Services rychlý Start)

Toto je konečný úkol pro rychlý Start WCF Data Services. V této úloze přidáte do řešení konzolovou aplikaci, do této nové klientské aplikace přidáte odkaz na [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informační kanál a získáte přístup k datovému kanálu OData z klientské aplikace pomocí generovaných tříd klientské datové služby a klientských knihoven. .

> [!NOTE]
> Klientská aplikace založená na .NET Framework není nutná pro přístup k datovému kanálu. Datová služba je k dispozici pro libovolnou komponentu aplikace, která využívá datový kanál OData. Další informace najdete v tématu [použití datové služby v klientské aplikaci](using-a-data-service-in-a-client-application-wcf-data-services.md).

## <a name="to-create-the-client-application-by-using-visual-studio"></a>Vytvoření klientské aplikace pomocí sady Visual Studio

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na řešení, klikněte na tlačítko **Přidat**a poté klikněte na možnost **Nový projekt**.

2. V levém podokně vyberte **nainstalované** > [ **C# Visual** nebo **Visual Basic**] > **Windows Desktop**a pak vyberte šablonu **aplikace WPF** .

3. Jako `NorthwindClient` název projektu zadejte a klikněte na **OK**.

4. Otevřete soubor MainWindow. XAML a nahraďte kód XAML následujícím kódem:

     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml#window1xaml)]

## <a name="to-add-a-data-service-reference-to-the-project"></a>Přidání odkazu na datovou službu do projektu

1. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt NorthwindClient, klikněte na **Přidat** > **odkaz na službu**a pak klikněte na **Vyhledat**.

     Tím se zobrazí datová služba Northwind, kterou jste vytvořili v prvním úkolu.

2. Do textového pole **obor názvů** zadejte `Northwind`a klikněte na **OK**.

     Tím se do projektu přidá nový soubor kódu, který obsahuje datové třídy, které slouží k přístupu k prostředkům datové služby a k interakci s nimi. Datové třídy jsou vytvořeny v oboru názvů `NorthwindClient.Northwind`.

## <a name="to-access-data-service-data-in-the-wpf-application"></a>Přístup k datům datové služby v aplikaci WPF

1. V **Průzkumník řešení** v části **NorthwindClient**klikněte pravým tlačítkem na projekt a klikněte na **Přidat odkaz**.

2. V dialogovém okně **Přidat odkaz** klikněte na kartu **.NET** , vyberte sestavení System. data. Services. Client. dll a potom klikněte na tlačítko **OK**.

3. V **Průzkumník řešení** v části **NorthwindClient**otevřete znakovou stránku souboru MainWindow. XAML a přidejte následující `using` příkaz (`Imports` v Visual Basic).

    [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#using)]
    [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#using)]

4. Vložte následující kód, který odešle dotaz na datovou službu a vytvoří vazby výsledku k <xref:System.Data.Services.Client.DataServiceCollection%601> `MainWindow` do třídy:

    > [!NOTE]
    > Je nutné nahradit název `localhost:12345` hostitele serverem a portem, který je hostitelem vaší instance datové služby Northwind.

     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#querycode)]

5. Vložte následující kód, který ukládá změny do `MainWindow` třídy:

     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#savechanges)]

## <a name="to-build-and-run-the-northwindclient-application"></a>Sestavení a spuštění aplikace NorthwindClient

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt NorthwindClient a vyberte **nastavit jako spouštěný projekt**.

2. Stisknutím klávesy **F5** spusťte aplikaci.

     Tím se vytvoří řešení a spustí se klientská aplikace. Služba požaduje data, která se zobrazí v konzole nástroje.

3. Upravte hodnotu ve sloupci **množství** datové mřížky a pak klikněte na **Uložit**.

     Změny se uloží do datové služby.

    > [!NOTE]
    > Tato verze aplikace NorthwindClient nepodporuje přidávání a odstraňování entit.

## <a name="next-steps"></a>Další kroky

Úspěšně jste vytvořili klientskou aplikaci, která přistupuje k ukázkovému informačnímu kanálu OData Northwind. Dokončili jste také rychlý Start WCF Data Services.

Další informace o přístupu k datovému kanálu OData z .NET Framework aplikace najdete v tématu [WCF Data Services Klientská knihovna](wcf-data-services-client-library.md).

## <a name="see-also"></a>Viz také:

- [Začínáme](getting-started-with-wcf-data-services.md)
- [Prostředky](wcf-data-services-resources.md)
