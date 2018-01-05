---
title: "Postupy: vytvoření služby pracovního postupu, který využívá existující smlouvy služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a754875dc3f7968086f4f92044205b8ebceb01e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a>Postupy: vytvoření služby pracovního postupu, který využívá existující smlouvy služby
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]Funkce lepší integrace mezi webové služby a pracovní postupy ve formě vývoj kontrakt první pracovního postupu. Nástroj pro vývoj kontrakt první pracovního postupu můžete navrhnout první kontrakt v kódu. Nástroj potom automaticky generuje šablonu aktivit v sadě nástrojů pro operace v kontraktu.  
  
> [!NOTE]
>  Toto téma obsahuje podrobné pokyny k vytvoření pracovního postupu první kontrakt služby. [!INCLUDE[crabout](../../../includes/crabout-md.md)]vývoj pracovního postupu první kontraktu služby, najdete v části [kontrakt první pracovní postup služby vývoj](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md).  
  
### <a name="creating-the-workflow-project"></a>Vytvoření projektu pracovního postupu  
  
1.  V [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], vyberte **soubor**, **nový projekt**. Vyberte **WCF** pod uzlem **C#** uzel v **šablony** stromu a vyberte **aplikace služby pracovního postupu WCF** šablony.  
  
2.  Název nového projektu `ContractFirst` a klikněte na tlačítko **Ok**.  
  
### <a name="creating-the-service-contract"></a>Vytvoření kontraktu služby  
  
1.  Klikněte pravým tlačítkem na projekt v **Průzkumníku řešení** a vyberte **přidat**, **novou položku...** . Vyberte **kód** uzlu na levé straně a **třída** šablony na pravé straně. Pojmenujte novou třídu `IBookService` a klikněte na tlačítko **Ok**.  
  
2.  V horní části okna kód, který se zobrazí, přidejte příkaz Using k `System.Servicemodel`.  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3.  Definice třídy ukázka změňte na následující definici rozhraní.  
  
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
  
4.  Sestavení projektu stisknutím **Ctrl + Shift + B**.  
  
### <a name="importing-the-service-contract"></a>Import kontrakt služby  
  
1.  Klikněte pravým tlačítkem na projekt v **Průzkumníku řešení** a vyberte **kontrakt služby Import**. V části  **\<aktuální projekt >**otevřete všech podřízených uzlů a vyberte **IBookService**. Click **OK**.  
  
2.  Otevře se dialogové okno, které výstrahy upozorňující, že se operace dokončila úspěšně a že generované aktivity se zobrazí v panelu nástrojů po sestavení projektu. Click **OK**.  
  
3.  Sestavení projektu stisknutím **Ctrl + Shift + B**tak, aby importované aktivity se zobrazí v panelu nástrojů.  
  
4.  V **Průzkumníku**, otevřete Service1.xamlx. Pracovní postup služby se zobrazí v návrháři.  
  
5.  Vyberte **pořadí** aktivity. V okně vlastností klikněte **...** tlačítko v **ImplementedContract** vlastnost. V **Editor kolekce typ** okno, které se zobrazí, klikněte na tlačítko **typ** rozevíracího seznamu a vyberte **Procházet pro typy...** položka. V **Procházet a vyberte .net zadejte** dialogové okno, v části  **\<aktuální projekt >**otevřete všech podřízených uzlů a vyberte **IBookService**. Click **OK**. V **Editor kolekce typ** dialogové okno, klikněte na tlačítko **OK**.  
  
6.  Vyberte a odstraňte **ReceiveRequest** a **SendResponse** aktivity.  
  
7.  Ze sady nástrojů, přetáhněte **Buy_ReceiveAndSendReply** a **Checkout_Receive** aktivity na **sekvenční služby** aktivity.
