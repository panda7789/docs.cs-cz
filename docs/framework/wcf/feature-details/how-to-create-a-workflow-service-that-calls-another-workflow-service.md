---
title: 'Postupy: Vytvoření služby pracovních postupů, která volá jinou službu pracovních postupů'
ms.date: 03/30/2017
ms.assetid: 99b3ee3e-aeb7-4e6f-8321-60fe6140eb67
ms.openlocfilehash: 1b30da34f7c85cccd98b18cd32b81c83630989b2
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44080212"
---
# <a name="how-to-create-a-workflow-service-that-calls-another-workflow-service"></a>Postupy: Vytvoření služby pracovních postupů, která volá jinou službu pracovních postupů

Někdy je nezbytné služby pracovního postupu k získání informací z jiné služby pracovního postupu. Toto téma ukazuje, jak z jiného volání jedné služby pracovního postupu. V tomto tématu vytvoříme dvě služby pracovního postupu; jeden, který obsahuje metodu, která obrací vstupního řetězce a druhý, který převede vstupní řetězec na velká písmena po vrácení řetězec, který používá službu první.

### <a name="to-create-the-reverser-workflow-service"></a>Vytvoření služby pracovního postupu Reverser

1.  Otevřít Visual Studio.

2.  Vyberte **souboru** > **nový projekt**. V části **pracovního postupu** uzlu **nainstalované šablony** vyberte **aplikace služeb pracovního postupu WCF**. Pojmenujte řešení `NestedServices` a potom klikněte na tlačítko **OK**.

3.  V části **servery**, ujistěte se, že **použití místní webový Server IIS** zaškrtnuto. Klikněte na tlačítko **vytvořit virtuální adresář**. Klikněte na tlačítko **OK** v dialogové okno oznamující, že byl úspěšně vytvořen virtuální adresář.

4.  V Průzkumníku řešení, přejmenujte Service1.xamlx k `StringReverserService.xamlx`.

5.  Na **vlastnosti projektu** stránky pro nový projekt, klikněte na tlačítko **webové** kartu. Nastavte **spustit akci** k **konkrétní stránka**a vyberte StringReverserService.xamlx jako stránky a spustit.

6.  V Návrháři otevřete StringReverserService.xamlx a odstranit existující `ReceiveRequest` a `SendReply` aktivit a pak přetáhněte `ReceiveAndSendReply` aktivity do existující sekvenční aktivity.

    1.  Nastavte **OperationName** k ReverseString.

    2.  Nastavte **ServiceContractName** k IReverseString.

    3.  Vyberte **CanCreateInstance** zaškrtávací políčko.

7.  Vyberte **SequentialService** aktivitu a pak klikněte na tlačítko **proměnné** karta v dolní části návrháře. Vytvořte dvě nové proměnné s názvem StringToReverse a ReversedStringToReturn typu String.

8.  Klikněte na tlačítko **definovat** odkaz v **Receive** aktivity. Klikněte na tlačítko **parametry**a vytvořit parametr s názvem InputString typu řetězec, který se přiřadí StringToReverse.

9. Klikněte na tlačítko **definovat** propojit **SendReplyToReceive** aktivity. Klikněte na tlačítko **parametry**a vytvořit parametr s názvem ReversedString typu String, přiřazená ReversedStringToReturn.

10. Implementovat logiku pro službu, vytvořte novou třídu v projektu volá StringLibrary.  Nahraďte definici třídy následujícím kódem.

    ```
    public class StringLibrary
        {
            public static String ReverseString(string StringToReverse)
            {
                char[] charArray = StringToReverse.ToCharArray();
                Array.Reverse(charArray);
                return new String(charArray);
            }
        }
    ```

11. Chcete-li volat metodu ReverseString na vstupu, přetáhněte **InvokeMethod** aktivitu z panelu nástrojů do prostoru mezi **Receive** a **odeslání odpovědi SendReply** aktivity. Nastavte vlastnosti aktivity následujícím způsobem:

    1.  **MethodName**: ReverseString

    2.  **Výsledek**: ReversedStringToReturn

    3.  **Parametry**: vytvoří nový parametr s **směr** nástroje v aplikaci, **typ** řetězce a **hodnota** z StringToReverse.

    4.  **TargetType**: NestedServices.StringLibrary

12. Pokud chcete službu otestujte stisknutím klávesy F5. Testovací klient WCF, který se zobrazí klikněte dvakrát na metodu ReverseString(). V podokně požadavku zadejte `Sample` pro hodnoty parametru InputString. Klikněte na tlačítko **vyvolat**. Služba by měla vrátit "elpmaS".

### <a name="to-create-the-uppercaser-workflow-service"></a>Vytvoření služby pracovního postupu UpperCaser

1.  Klikněte pravým tlačítkem na projekt NestedServices a vyberte **přidat** > **nová položka**. V **pracovního postupu** uzlu, vyberte **služby pracovního postupu WCF**a pojmenujte novou službu `UpperCaserService`. Klikněte na tlačítko **přidat**. To byste přidat nový pracovní postup služby zvané UpperCaserService.xamlx do projektu.

2.  V Návrháři otevřete UpperCaserService.xamlx a odstranit existující **ReceiveRequest** a `SendReply` aktivity a přetáhněte `ReceiveAndSendReply` aktivity do existující sekvenční aktivity.

    1.  Nastavte **OperationName** k UpperCaseString.

    2.  Nastavte **ServiceContractName** k IUpperCaseString.

    3.  Vyberte **CanCreateInstance** zaškrtávací políčko.

3.  Vybrat aktivitu SequentialService a potom klikněte na tlačítko **proměnné** karta v dolní části návrháře. Vytvořte tři nové proměnné s názvem StringToUpper StringToReverse a StringToReturn typu String.

4.  Klikněte na tlačítko **definovat** odkaz v **Receive** aktivity. Klikněte na tlačítko **parametry**a vytvořit parametr s názvem InputString typu řetězec, který se přiřadí StringToUpper.

5.  Klikněte na tlačítko **definovat** propojit **SendReplyToReceive** aktivity. Klikněte na tlačítko **parametry**a vytvořit parametr s názvem ModifiedString typu String, přiřazená StringToReturn.

6.  Pokud chcete implementovat logiku pro služby, vytvoření nové metody ve třídě StringLibrary pomocí následujícího kódu.

    ```
    public static String UpperCaseString(string StringToUpperCase)
    {
         return StringToUpperCase.ToUpper();

    }
    ```

7.  Chcete-li volat metodu UpperCaseString na vstupu, přetáhněte **InvokeMethod** aktivitu z panelu nástrojů do prostoru mezi **Receive** a **odeslání odpovědi SendReply** aktivity. Nastavte vlastnosti aktivity následujícím způsobem:

    1.  **MethodName**: UpperCaseString

    2.  **Výsledek**: StringToReverse

    3.  **Parametry**: vytvoří nový parametr s **směr** nástroje v aplikaci, **typ** řetězce a **hodnota** z StringToUpper.

    4.  **TargetType**: NestedServices.StringLibrary

8.  Nyní zavoláme vám první služby na upravený řetězec. Klikněte pravým tlačítkem na projekt a vyberte **přidat** > **odkaz na službu**. Přidání odkazu na službu na službu na http://localhost/NestedServices/StringReverserService.xamlx a sestavte projekt a vytvořit vlastní aktivitu pro přístup k webové službě první.

9. Přetáhněte instance novou aktivitu do pracovního postupu, mezi **InvokeMethod** aktivity a **SendReplyToReceive** aktivity. Přiřaďte proměnné StringToReverse vlastnost InputString nová aktivita a proměnné StringToReturn StringToReturn vlastnosti.

10. Otevřete stránku vlastností pro projekt NestedServices a změnit **konkrétní stránka** v **webové** kartu UpperCaserService.xamlx.

11. Pokud chcete službu otestujte stisknutím klávesy F5. Testovací klient WCF, který se zobrazí klikněte dvakrát na metodu ReverseString(). V podokně požadavku zadejte `Sample` pro hodnoty parametru InputString. Klikněte na tlačítko **vyvolat**. Služba by měla vrátit "ELPMAS".

### <a name="to-create-a-client-to-call-the-services"></a>K vytvoření klienta k volání služeb

1.  Přidáte nový projekt konzolové aplikace volá klienta do řešení.

2.  Klikněte pravým tlačítkem na klientský projekt a vyberte **přidat** > **odkaz na službu**. V okně, které se zobrazí, klikněte na tlačítko **Discover**. Vyberte StringReverserService.xamlx a zadejte ReverseService jako obor názvů.  Klikněte na tlačítko **OK**.

3.  Metoda Main v souboru Program.cs nahraďte následujícím kódem.

    ```
    static void Main(string[] args)
    {
        Console.Write("Input string to process:");
        String input = Console.ReadLine();
        var service = new ReverseService.ReverseStringClient();
        Console.WriteLine("Output from service: {0}", service.ReverseString(input));
        Console.ReadKey();
    }
    ```