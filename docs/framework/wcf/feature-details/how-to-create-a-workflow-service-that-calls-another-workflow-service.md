---
title: 'Postupy: Vytvoření služby pracovních postupů, která volá jinou službu pracovních postupů'
ms.date: 03/30/2017
ms.assetid: 99b3ee3e-aeb7-4e6f-8321-60fe6140eb67
ms.openlocfilehash: fda5a7286c3d20c7cdc2093e58bfe3fbdcf1d1c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497188"
---
# <a name="how-to-create-a-workflow-service-that-calls-another-workflow-service"></a>Postupy: Vytvoření služby pracovních postupů, která volá jinou službu pracovních postupů
Někdy je nezbytné pro služby pracovního postupu, který chcete získat informace z jiné služby pracovního postupu.  Toto téma ukazuje, jak volat jeden služby pracovního postupu z druhého. V tomto tématu vytvoříme dvě služby pracovního postupu; ten, který má metodu, která obrátí vstupní řetězec a druhý, který převádí vstupního řetězce na velká písmena po Prohodit řetězec, který používá službu první.  
  
### <a name="to-create-the-reverser-workflow-service"></a>Vytvoření služby pracovního postupu Reverser  
  
1.  Spustit [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] jako správce.  
  
2.  Vyberte **soubor**, **nový projekt**. V části **pracovního postupu** uzel v **nainstalovaných šablonách** podokně, vyberte **aplikace služby pracovního postupu WCF**. Název řešení `NestedServices` a pak klikněte na **OK**.  
  
3.  V části **servery**, ujistěte se, že **použití místního webového serveru IIS** je vybrána. Klikněte na tlačítko **vytvořit virtuální adresář**. Klikněte na tlačítko **OK** v dialogovém okně pole oznamující, že byl úspěšně vytvořen virtuální adresář.  
  
4.  V Průzkumníku řešení, přejmenujte Service1.xamlx k `StringReverserService.xamlx`.  
  
5.  Na **vlastnosti projektu** stránky pro nový projekt, klikněte na tlačítko **webové** kartě. Nastavte **spustit akci** k **konkrétní stránky**a vyberte StringReverserService.xamlx jako stránku a spustit.  
  
6.  Otevřete StringReverserService.xamlx v návrháři a odstranit existující `ReceiveRequest` a `SendReply` aktivity a pak přetáhněte `ReceiveAndSendReply` aktivity do existující aktivitu pořadí.  
  
    1.  Nastavte **OperationName** k ReverseString.  
  
    2.  Nastavte **ServiceContractName** k IReverseString.  
  
    3.  Vyberte **CanCreateInstance** zaškrtávací políčko.  
  
7.  Vyberte **SequentialService** aktivitu a klikněte **proměnné** karta v dolní části návrháře. Vytvořte dva nové proměnné s názvem StringToReverse a ReversedStringToReturn typu řetězec.  
  
8.  Klikněte na tlačítko **definovat** na odkaz v **Receive** aktivity. Klikněte **parametry**a vytvořte parametr s názvem InputString typu řetězec, který přiřazuje StringToReverse.  
  
9. Klikněte **definovat** na odkaz v **SendReplyToReceive** aktivity. Klikněte **parametry**a vytvořte parametr s názvem ReversedString typu řetězec, přiřazené ReversedStringToReturn.  
  
10. Pokud chcete implementovat logiku pro službu, vytvořte novou třídu do projektu názvem StringLibrary.  Nahraďte definici třídy následujícím kódem.  
  
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
  
11. K volání metody ReverseString na vstupu, přetáhněte **InvokeMethod** aktivity z panelu nástrojů do prostoru mezi **Receive** a **SendReply** aktivity. Nastavte vlastnosti aktivity následujícím způsobem:  
  
    1.  **MethodName**: ReverseString  
  
    2.  **Výsledek**: ReversedStringToReturn  
  
    3.  **Parametry**: Vytvořte nový parametr s **směr** z v, **typ** řetězce a **hodnotu** z StringToReverse.  
  
    4.  **TargetType**: NestedServices.StringLibrary  
  
12. Testování služby stisknutím klávesy F5. V testovacího klienta WCF, který se zobrazí klikněte dvakrát na metodu ReverseString(). V podokně požadavek zadejte `Sample` pro hodnotu parametru InputString. Klikněte na tlačítko **vyvolání**. Služba by měl vrátit "elpmaS".  
  
### <a name="to-create-the-uppercaser-workflow-service"></a>Vytvoření služby pracovního postupu UpperCaser  
  
1.  Klikněte pravým tlačítkem na projekt NestedServices a vyberte **přidat**, **novou položku**. V **pracovního postupu** uzlu, vyberte **pracovního postupu služby WCF**a název nové služby `UpperCaserService`. Klikněte na tlačítko **přidat**. To měli přidat novou službu pracovního postupu s názvem UpperCaserService.xamlx do projektu.  
  
2.  Otevřete UpperCaserService.xamlx v návrháři a odstranit existující **ReceiveRequest** a `SendReply` aktivity a přetažení `ReceiveAndSendReply` aktivity do existující aktivitu pořadí.  
  
    1.  Nastavte **OperationName** k UpperCaseString.  
  
    2.  Nastavte **ServiceContractName** k IUpperCaseString.  
  
    3.  Vyberte **CanCreateInstance** zaškrtávací políčko.  
  
3.  Vyberte aktivitu SequentialService a klikněte **proměnné** karta v dolní části návrháře. Vytvořte tři nové proměnné s názvem StringToUpper, StringToReverse a StringToReturn typu řetězec.  
  
4.  Klikněte na tlačítko **definovat** na odkaz v **Receive** aktivity. Klikněte **parametry**a vytvořte parametr s názvem InputString typu řetězec, který přiřazuje StringToUpper.  
  
5.  Klikněte **definovat** na odkaz v **SendReplyToReceive** aktivity. Klikněte **parametry**a vytvořte parametr s názvem ModifiedString typu řetězec, přiřazené StringToReturn.  
  
6.  Pokud chcete implementovat logiku pro službu, vytvoření nové metody ve třídě StringLibrary pomocí následujícího kódu.  
  
    ```  
    public static String UpperCaseString(string StringToUpperCase)  
    {  
         return StringToUpperCase.ToUpper();  
  
    }  
    ```  
  
7.  K volání metody UpperCaseString na vstupu, přetáhněte **InvokeMethod** aktivity z panelu nástrojů do prostoru mezi **Receive** a **SendReply** aktivity. Nastavte vlastnosti aktivity následujícím způsobem:  
  
    1.  **MethodName**: UpperCaseString  
  
    2.  **Výsledek**: StringToReverse  
  
    3.  **Parametry**: Vytvořte nový parametr s **směr** z v, **typ** řetězce a **hodnotu** z StringToUpper.  
  
    4.  **TargetType**: NestedServices.StringLibrary  
  
8.  Nyní zavoláme vám první službě na upravené řetězec. Klikněte pravým tlačítkem na projekt a vyberte **přidat odkaz na službu**. Přidat odkaz na službu na službu na http://localhost/NestedServices/StringReverserService.xamlx a sestavte projekt a vytvořit vlastní aktivitu pro přístup k první webové služby.  
  
9. Přetáhněte instanci novou aktivitu do pracovního postupu, mezi **InvokeMethod** aktivity a **SendReplyToReceive** aktivity. Přiřaďte proměnnou StringToReverse vlastnost InputString nová aktivita a proměnné StringToReturn pro vlastnost StringToReturn.  
  
10. Otevřete stránku vlastností projektu NestedServices a změňte **konkrétní stránky** v **webové** a UpperCaserService.xamlx.  
  
11. Testování služby stisknutím klávesy F5. V testovacího klienta WCF, který se zobrazí klikněte dvakrát na metodu ReverseString(). V podokně požadavek zadejte `Sample` pro hodnotu parametru InputString. Klikněte na tlačítko **vyvolání**. Služba by měl vrátit "ELPMAS".  
  
### <a name="to-create-a-client-to-call-the-services"></a>Chcete-li vytvořit klienta k volání služeb  
  
1.  Přidáte nový projekt konzolové aplikace volá klienta k řešení.  
  
2.  Klikněte pravým tlačítkem na projekt klienta a vyberte **přidat odkaz na službu**. V okně, které se zobrazí, klikněte na **Discover**. Vyberte StringReverserService.xamlx a zadejte ReverseService jako obor názvů.  Click **OK**.  
  
3.  Nahraďte metodu Main v souboru Program.cs následujícím kódem.  
  
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
