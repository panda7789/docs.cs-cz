---
title: 'Kurz: Definování smlouvy o poskytování služeb Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 7c1c42c4f22a1a9627c147440e8e198551470b7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184095"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>Kurz: Definování smlouvy o poskytování služeb Windows Communication Foundation

Tento kurz popisuje první z pěti úloh potřebných k vytvoření základní aplikace Windows Communication Foundation (WCF). Přehled výukových programů najdete v [tématu Výuka: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md).

Při vytváření služby WCF je vaším prvním úkolem definovat servisní smlouvu. Servisní smlouva určuje, jaké operace služba podporuje. Operaci lze považovat za metodu webové služby. Servisní smlouvy vytvoříte definováním rozhraní jazyka C# nebo jazyka Visual Basic. Rozhraní má následující charakteristiky:

- Každá metoda v rozhraní odpovídá konkrétní operaci služby.
- Pro každé rozhraní je <xref:System.ServiceModel.ServiceContractAttribute> nutné použít atribut.
- Pro každou operaci/metodu je <xref:System.ServiceModel.OperationContractAttribute> nutné použít atribut.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Vytvořte projekt **knihovny služeb WCF.**
> - Definujte rozhraní servisní smlouvy.

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>Vytvoření projektu knihovny služeb WCF a definování rozhraní servisní smlouvy

1. Otevřete Visual Studio jako správce. Chcete-li tak učinit, vyberte program sady Visual Studio v nabídce **Start** a v místní nabídce vyberte možnost **Další** > **spuštění jako správce.**

2. Vytvořte projekt **knihovny služeb WCF.**

   1. V nabídce **Soubor** vyberte **Nový** > **projekt**.

   2. V dialogovém okně **Nový projekt** rozbalte na levé straně **položku Visual C#** nebo **Visual Basic**a vyberte kategorii **WCF.** Visual Studio zobrazí seznam šablon projektů ve středové části okna. Vyberte **knihovnu služeb WCF**.

      > [!NOTE]
      > Pokud nevidíte kategorii šablony projektu **WCF,** bude pravděpodobně nutné nainstalovat součást **Windows Communication Foundation** sady Visual Studio. V dialogovém okně **Nový projekt** vyberte na levé straně odkaz Otevřít instalační program sady **Visual Studio.** Vyberte kartu **Jednotlivé součásti** a v kategorii **Aktivity vývoje** vyberte a vyberte **Windows Communication Foundation.** Chcete-li začít instalovat komponentu, zvolte **Změnit.**

   3. V dolní části okna zadejte *GettingStartedLib* pro **název** a *GettingStarted* pro **název řešení**.

   4. Vyberte **OK**.

      Visual Studio vytvoří projekt, který má tři soubory: *IService1.cs* (nebo *IService1.vb* pro projekt jazyka), *Service1.cs* (nebo *Service1.vb* pro projekt jazyka Visual Basic) a *App.config*. Visual Studio definuje tyto soubory takto:
      - Soubor *IService1* obsahuje výchozí definici servisní smlouvy.
      - Soubor *Service1* obsahuje výchozí implementaci servisní smlouvy.
      - Soubor *App.config* obsahuje informace o konfiguraci potřebné k načtení výchozí služby pomocí nástroje Host služby WCF sady Visual Studio. Další informace o nástroji WCF Service Host naleznete v tématu [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).

      > [!NOTE]
      > Pokud jste nainstalovali Visual Studio s nastavením prostředí pro vývojáře jazyka, řešení může být skryté. Pokud se jedná o tento případ, vyberte **možnosti** z nabídky **Nástroje** a v okně **Možnosti** vyberte**Projekty** **a obecně řešení.** >  Vyberte **možnost Vždy zobrazit řešení**. Ověřte také, zda je vybrána možnost **Uložit nové projekty při vytvoření.**

3. V **Průzkumníku řešení**otevřete soubor **IService1.cs** nebo **IService1.vb** a nahraďte jeho kód následujícím kódem:

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

     Tato smlouva definuje online kalkulačku. Všimněte `ICalculator` si, že <xref:System.ServiceModel.ServiceContractAttribute> rozhraní je `ServiceContract`označeno atributem (zjednodušeno jako ). Tento atribut definuje obor názvů, aby se název smlouvy rozpodomoval. Kód označí každou <xref:System.ServiceModel.OperationContractAttribute> operaci kalkulačky `OperationContract`atributem (zjednodušeným jako).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> - Vytvořte projekt knihovny služeb WCF.
> - Definujte rozhraní servisní smlouvy.

Přejdete k dalšímu kurzu, který se dozvíte, jak implementovat servisní smlouvu WCF.

> [!div class="nextstepaction"]
> [Kurz: Implementace smlouvy o poskytování služeb WCF](how-to-implement-a-wcf-contract.md)
