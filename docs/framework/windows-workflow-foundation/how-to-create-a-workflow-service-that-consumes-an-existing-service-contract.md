---
title: 'Postupy: Vytvoření služby pracovního postupu, která využívá existující kontrakt služby'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: c2ca9c349718c3939d74d052ff0ed448879cd045
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945571"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a>Postupy: Vytvoření služby pracovního postupu, která využívá existující kontrakt služby
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Funkce lepší integrace mezi službami webové a pracovní postupy ve formuláři stavící do pracovního postupu vývoje. Pracovní postup kontraktem vývojový nástroj umožňuje navrhovat smlouvy v kódu. Nástroj potom automaticky vygeneruje šablonu aktivit v sadě nástrojů pro operace v kontraktu.  
  
> [!NOTE]
>  Toto téma obsahuje podrobné pokyny k vytváření služby stavící do pracovního postupu. Další informace o vývoj služby stavící do pracovního postupu najdete v tématu [nasazení služby pracovního postupu prvního kontraktu](contract-first-workflow-service-development.md).  
  
### <a name="creating-the-workflow-project"></a>Vytvoření projektu pracovního postupu  
  
1. V sadě Visual Studio, vyberte **souboru**, **nový projekt**. Vyberte **WCF** pod uzlem **C#** uzlu **šablony** stromu a vyberte **aplikace služeb pracovního postupu WCF** Šablona.  
  
2. Název nového projektu `ContractFirst` a klikněte na tlačítko **Ok**.  
  
### <a name="creating-the-service-contract"></a>Vytvoření kontraktu služby  
  
1. Klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a vyberte **přidat**, **novou položku...** . Vyberte **kód** uzlu na levé straně a **třídy** šablon na pravé straně. Pojmenujte novou třídu `IBookService` a klikněte na tlačítko **Ok**.  
  
2. V horní části okna kódu, který se zobrazí, přidejte příkaz Using do `System.Servicemodel`.  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3. Ukázková definice třídy změňte na následující definici rozhraní.  
  
    ```  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4. Sestavte projekt stisknutím kombinace kláves **Ctrl + Shift + B**.  
  
### <a name="importing-the-service-contract"></a>Importuje se kontrakt služby  
  
1. Klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a vyberte **importovat kontrakt služby**. V části  **\<aktuální projekt >**, otevřete všechny dílčí uzlů a vyberte **IBookService**. Klikněte na **OK**.  
  
2. Otevře se dialogové okno, upozorní vás, operace byla úspěšně dokončena a že generované aktivity se zobrazí na panelu nástrojů po sestavení projektu. Klikněte na **OK**.  
  
3. Sestavte projekt stisknutím kombinace kláves **Ctrl + Shift + B**tak, aby importovaná aktivity se zobrazí na panelu nástrojů.  
  
4. V **Průzkumníka řešení**, otevřete Service1.xamlx. Služba pracovního postupu se zobrazí v návrháři.  
  
5. Vyberte **pořadí** aktivity. V okně Vlastnosti klikněte na tlačítko **...** tlačítko **ImplementedContract** vlastnost. V **Editor typu kolekce** okno, které se zobrazí, klikněte **typ** rozevíracím seznamu a vyberte **vyhledat typy...** položka. V **Procházet a vybrat typ .NET** dialogového okna, v části  **\<aktuální projekt >**, otevřete všechny dílčí uzlů a vyberte **IBookService**. Klikněte na **OK**. V **Editor typu kolekce** dialogového okna, klikněte na tlačítko **OK**.  
  
6. Vyberte a odstraňte **ReceiveRequest** a **SendResponse** aktivity.  
  
7. Z panelu nástrojů přetáhněte **Buy_ReceiveAndSendReply** a **Checkout_Receive** aktivity do **sekvenční služba** aktivity.
