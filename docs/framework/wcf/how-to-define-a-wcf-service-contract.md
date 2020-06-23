---
title: 'Kurz: Definování kontraktu Windows Communication Foundation služby'
description: Naučte se definovat kontrakt služby jako součást série článků, které vám pomůžou začít vytvářet aplikace WCF.
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 5cb371da8c7180b8c4cbf5ac11468fbb8e0e13cc
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246308"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>Kurz: Definování kontraktu Windows Communication Foundation služby

Tento kurz popisuje prvních pět úloh nutných k vytvoření aplikace Basic Windows Communication Foundation (WCF). Přehled kurzů najdete v tématu [kurz: Začínáme s Windows Communication Foundation aplikacemi](getting-started-tutorial.md).

Při vytváření služby WCF je vaším prvním úkolem Definování kontraktu služby. Kontrakt služby určuje, které operace služba podporuje. Operaci lze představit jako metodu webové služby. Kontrakty služby vytvoříte definováním rozhraní C# nebo Visual Basic. Rozhraní má následující vlastnosti:

- Každá metoda v rozhraní odpovídá konkrétní operaci služby.
- Pro každé rozhraní je nutné použít <xref:System.ServiceModel.ServiceContractAttribute> atribut.
- Pro každou operaci/metodu je nutné použít <xref:System.ServiceModel.OperationContractAttribute> atribut.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Vytvořte projekt **knihovny služby WCF** .
> - Definujte rozhraní kontraktu služby.

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>Vytvoření projektu knihovny služby WCF a definování rozhraní kontraktu služby

1. Otevřete Visual Studio jako správce. Provedete to tak, že v nabídce **Start** vyberete program Visual Studio a v místní nabídce vyberete **Další**  >  **Spustit jako správce** .

2. Vytvořte projekt **knihovny služby WCF** .

   1. V nabídce **soubor** vyberte možnost **Nový**  >  **projekt**.

   2. V dialogovém okně **Nový projekt** , na levé straně, rozbalte položku **Visual C#** nebo **Visual Basic**a pak vyberte kategorii **WCF** . Visual Studio zobrazí seznam šablon projektů v části Center v okně. Vyberte **knihovnu služby WCF**.

      > [!NOTE]
      > Pokud nevidíte kategorii šablony projektů **WCF** , bude pravděpodobně nutné nainstalovat **Windows Communication Foundation** součást sady Visual Studio. V dialogovém okně **Nový projekt** vyberte odkaz **otevřít instalační program pro Visual Studio** na levé straně. Vyberte kartu **jednotlivé součásti** a v kategorii **vývojové aktivity** vyhledejte a vyberte **Windows Communication Foundation** . Chcete-li zahájit instalaci komponenty, klikněte na tlačítko **Upravit** .

   3. V dolní části okna zadejte *GettingStartedLib* pro **název** a *soubor GettingStarted* pro **název řešení**.

   4. Vyberte **OK**.

      Visual Studio vytvoří projekt, který má tři soubory: *IService1.cs* (nebo *IService1. vb* pro projekt Visual Basic), *Service1.cs* (nebo *Service1. vb* pro Visual Basic projekt) a *App.config*. Visual Studio definuje tyto soubory následujícím způsobem:
      - Soubor *IService1* obsahuje výchozí definici kontraktu služby.
      - Soubor *Service1* obsahuje výchozí implementaci kontraktu služby.
      - *App.config* soubor obsahuje informace o konfiguraci potřebné k načtení výchozí služby pomocí nástroje pro hostování služby Visual Studio WCF. Další informace o nástroji pro hostování služby WCF najdete v tématu [Hostitel služby WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).

      > [!NOTE]
      > Pokud jste nainstalovali Visual Studio s Visual Basic nastavení vývojářského prostředí, řešení může být skryté. Pokud se jedná o tento případ, vyberte **Možnosti** v nabídce **nástroje** a pak v okně Možnosti vyberte **projekty a řešení**  >  **Obecné** . **Options** Vyberte možnost **vždy zobrazit řešení**. Ověřte také, že je vybrána možnost **Uložit nové projekty při vytvoření** .

3. Z **Průzkumník řešení**otevřete soubor **IService1.cs** nebo **IService1. vb** a nahraďte jeho kód následujícím kódem:

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

     Tato Smlouva definuje online kalkulačku. Všimněte si, že `ICalculator` rozhraní je označeno <xref:System.ServiceModel.ServiceContractAttribute> atributem (zjednodušeno jako `ServiceContract` ). Tento atribut definuje obor názvů pro jednoznačnost názvu kontraktu. Kód označí každou operaci kalkulačky <xref:System.ServiceModel.OperationContractAttribute> atributem (zjednodušeno jako `OperationContract` ).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> - Vytvořte projekt knihovny služby WCF.
> - Definujte rozhraní kontraktu služby.

Přejděte k dalšímu kurzu, kde se dozvíte, jak implementovat kontrakt služby WCF.

> [!div class="nextstepaction"]
> [Kurz: implementace kontraktu služby WCF](how-to-implement-a-wcf-contract.md)
