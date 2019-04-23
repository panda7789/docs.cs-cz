---
title: 'Kurz: Definování kontraktu služby Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: a1908339460191fcb81d03d45c56dd57b2cf4c4e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228390"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>Kurz: Definování kontraktu služby Windows Communication Foundation

Tento kurz popisuje prvních pět úloh potřebných k vytvoření základní aplikace Windows Communication Foundation (WCF). Přehled v kurzech, naleznete v tématu [kurzu: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md).

Při vytváření služeb WCF je první úkol k definování kontraktu služby. Kontrakt služby specifikuje, jaké operace služba podporuje. Operace můžete představit jako metodu webové služby. Vytváření kontraktů služby tak, že definujete Vizuálu C# nebo rozhraní jazyka Visual Basic (VB). Rozhraní má následující vlastnosti:

- Každá metoda v rozhraní odpovídá konkrétní operaci služby. 
- Pro každé rozhraní, musíte použít <xref:System.ServiceModel.ServiceContractAttribute> atribut.
- Pro každou operaci/metodu, musíte použít <xref:System.ServiceModel.OperationContractAttribute> atribut. 

V tomto kurzu se naučíte:
> [!div class="checklist"]
> - Vytvoření **knihovny služby WCF** projektu.
> - Definujte rozhraní kontraktu služby.

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>Vytvořte projekt knihovny služby WCF a definování rozhraní kontraktu služby

1. Otevřít Visual Studio jako správce. Pokud chcete udělat, vyberte program sady Visual Studio v **Start** nabídky a pak vyberte **Další** > **spustit jako správce** z místní nabídky.

2. Vytvoření **knihovny služby WCF** projektu.

   1. Z **souboru** nabídce vyberte možnost **nový** > **projektu**.

   2. V **nový projekt** na levé straně dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic**a pak vyberte **WCF** kategorie. Visual Studio zobrazí seznam šablon projektů v části System center okna. Vyberte **knihovny služby WCF**.

      > [!NOTE]
      > Pokud se nezobrazí **WCF** kategorii šablony projektu, budete muset nainstalovat **Windows Communication Foundation** komponentu sady Visual Studio. V **nový projekt** dialogové okno, vyberte **otevřít instalační program Visual Studio** odkazu na levé straně. Vyberte **jednotlivé komponenty** kartu a potom najděte a vyberte **Windows Communication Foundation** pod **vývojových aktivit** kategorie. Zvolte **změnit** zahájíte instalaci komponenty.

   3. V dolní části okna, zadejte *GettingStartedLib* pro **název** a *GettingStarted* pro **název řešení**. 

   4. Vyberte **OK**.

      Visual Studio vytvoří projekt, který má tři soubory: *IService1.cs* (nebo *IService1.vb* pro projekt jazyka Visual Basic), *Service1.cs* (nebo *Service1.vb* pro projekt jazyka Visual Basic), a  *App.config*. Visual Studio definuje tyto soubory následujícím způsobem: 
      - *IService1* soubor obsahuje výchozí definici kontraktu služby. 
      - *Service1* soubor obsahuje výchozí implementace kontraktu služby. 
      - *App.config* soubor obsahuje informace o konfiguraci potřebné k načtení výchozí služby pomocí nástroje Visual Studio WCF služby hostitele. Další informace o nástroji pro hostitele služby WCF najdete v tématu [hostitel služby WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).

      > [!NOTE]
      > Pokud jste nainstalovali aplikaci Visual Studio pomocí nastavení prostředí pro vývojáře jazyka Visual Basic, může být skrytá řešení. Pokud je to tento případ, vyberte **možnosti** z **nástroje** nabídce pak vyberte **projekty a řešení** > **Obecné** v **možnosti** okna. Vyberte **vždy zobrazit řešení**. Kromě toho ověřte, že **uložit nové projekty při vytvoření** zaškrtnuto.

3. Z **Průzkumníka řešení**, otevřete **IService1.cs** nebo **IService1.vb** souboru a jeho kódu nahraďte následujícím kódem:

    ```csharp
    using System;
    using System.ServiceModel;

    namespace GettingStartedLib
    {
            [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
            public interface ICalculator
            {
                [OperationContract]
                double Add(double n1, double n2);
                [OperationContract]
                double Subtract(double n1, double n2);
                [OperationContract]
                double Multiply(double n1, double n2);
                [OperationContract]
                double Divide(double n1, double n2);
            }
    }
    ```

    ```vb
    Imports System.ServiceModel

    Namespace GettingStartedLib

        <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
        Public Interface ICalculator

            <OperationContract()> _
            Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
        End Interface
    End Namespace
    ```

     Tento kontrakt definuje online kalkulačku. Všimněte si, že `ICalculator` rozhraní je označeno příznakem s <xref:System.ServiceModel.ServiceContractAttribute> atribut (zjednodušené jako `ServiceContract`). Tento atribut definuje obor názvů k rozlišení názvu kontraktu. Kód označuje každá operace kalkulačky s <xref:System.ServiceModel.OperationContractAttribute> atribut (zjednodušené jako `OperationContract`).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
> - Vytvořte projekt knihovny služby WCF.
> - Definujte rozhraní kontraktu služby.

Přejděte k dalšímu kurzu se naučíte implementace kontraktu služby WCF.

> [!div class="nextstepaction"]
> [Kurz: Implementace kontraktu služby WCF](how-to-implement-a-wcf-contract.md)
