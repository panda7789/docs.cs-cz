---
title: 'Postupy: Definování kontraktu služby WCF'
ms.date: 09/14/2018
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 4f85a51c47eb045d1d2f0111cb217199c9acf0d7
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46009005"
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a>Postupy: Definování kontraktu služby WCF

Toto je první z šesti úkolů, muset vytvořit základní aplikaci Windows Communication Foundation (WCF). Přehled všech šesti úkoly, naleznete v tématu [kurz Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.

 Při vytváření služby WCF, je první úkol k definování kontraktu služby. Kontrakt služby specifikuje, jaké operace služba podporuje. Operace můžete představit jako metodu webové služby. Kontrakty se vytvoří definováním rozhraní C++, C# nebo Visual Basic (VB). Každá metoda v rozhraní odpovídá konkrétní operaci služby. Každé rozhraní musí mít <xref:System.ServiceModel.ServiceContractAttribute> použit a každá operace musí mít <xref:System.ServiceModel.OperationContractAttribute> byt aplikovaný atribut. Pokud metoda v rozhraní, který má <xref:System.ServiceModel.ServiceContractAttribute> atribut nemá <xref:System.ServiceModel.OperationContractAttribute> atribut, taková metoda se nevystaví službou.

 Kód použitý pro tuto úlohu je najdete v příkladu za postupem.

## <a name="define-a-service-contract"></a>Definování kontraktu služby

1. Otevřít Visual Studio jako správce kliknutím pravým tlačítkem myši v programu **Start** nabídky a vyberete **Další** > **spustit jako správce**.

2. Vytvořte projekt knihovny služby WCF.

   1. Z **souboru** nabídce vyberte možnost **nový** > **projektu**.

   2. V **nový projekt** na levé straně dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic**a pak vyberte **WCF** kategorie. V části System center dialogového okna se zobrazí seznam šablon projektů. Vyberte **knihovny služby WCF**.

   3. Zadejte `GettingStartedLib` v **název** textového pole a `GettingStarted` v **název řešení** textového pole v dolní části dialogového okna.

   > [!NOTE]
   > Pokud se nezobrazí **WCF** kategorii šablony projektu, budete muset nainstalovat **Windows Communication Foundation** komponentu sady Visual Studio. V **nový projekt** dialogovém okně klikněte na odkaz, který uvádí, že **otevřít instalační program Visual Studio**. Vyberte **jednotlivé komponenty** kartu a potom najděte a vyberte **Windows Communication Foundation** pod **vývojových aktivit** kategorie. Zvolte **změnit** zahájíte instalaci komponenty.

   Visual Studio vytvoří projekt, který obsahuje 3 soubory: IService1.cs (nebo IService1.vb) Service1.cs (nebo Service1.vb) a souboru App.config. Soubor IService1 obsahuje výchozí smlouvy o poskytování služeb. Soubor Service1 obsahuje výchozí implementace kontraktu služby. Soubor App.config obsahuje konfigurace, které jsou potřebné k načtení výchozí službu s Visual Studio hostitel služby WCF. Další informace o nástroji pro hostitele služby WCF najdete v tématu [hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)

3. Otevřete soubor IService1.cs nebo IService1.vb a odstranění kódu v rámci deklarace oboru názvů, byste museli opustit deklarace oboru názvů. Uvnitř oboru názvů deklarace definujte nové rozhraní s názvem `ICalculator` jak je znázorněno v následujícím kódu.

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

     Tento kontrakt definuje online kalkulačku. Všimněte si, že `ICalculator` rozhraní je označeno příznakem s <xref:System.ServiceModel.ServiceContractAttribute> atribut. Tento atribut definuje obor názvů, který se používá k rozlišení názvu kontraktu. Každá operace kalkulačky je označená pomocí <xref:System.ServiceModel.OperationContractAttribute> atribut.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Postupy: implementace kontraktu služby](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Postupy: Implementace kontraktu služby](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [Začínáme](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Vlastní hostování](../../../docs/framework/wcf/samples/self-host.md)