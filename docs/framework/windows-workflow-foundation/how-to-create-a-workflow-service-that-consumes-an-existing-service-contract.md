---
title: 'Postupy: Vytvoření služby pracovního postupu, která využívá existující kontrakt služby'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: f25e71aec03f9808b3263f0353328f92888ccc69
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962307"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a>Postupy: Vytvoření služby pracovního postupu, která využívá existující kontrakt služby
.NET Framework 4,5 nabízí lepší integraci mezi webovými službami a pracovními postupy ve formě vývoje pracovního postupu prvního kontraktu. Nástroj pro vývoj pracovního postupu prvního kontraktu vám umožní navrhnout kontrakt v kódu jako první. Nástroj pak na panelu nástrojů automaticky vygeneruje šablonu aktivity pro operace ve smlouvě.  
  
> [!NOTE]
> V tomto tématu najdete podrobné pokyny k vytvoření služby pracovního postupu pro první kontrakt. Další informace o vývoji služeb pracovního postupu prvního kontraktu najdete v tématu věnovaném [vývoji prvního pracovního postupu služby](contract-first-workflow-service-development.md).  
  
### <a name="creating-the-workflow-project"></a>Vytváření projektu pracovního postupu  
  
1. V aplikaci Visual Studio zvolte **soubor**, **Nový projekt**. V **C#** uzlu stromu **šablon** vyberte uzel **WCF** a vyberte šablonu **aplikace služby pracovního postupu WCF** .  
  
2. Pojmenujte nový `ContractFirst` projekt a klikněte na **OK**.  
  
### <a name="creating-the-service-contract"></a>Vytváření kontraktu služby  
  
1. Klikněte pravým tlačítkem na projekt v **Průzkumník řešení** a vyberte **Přidat**, **Nová položka.** . Vyberte uzel **kódu** na levé straně a šablonu **třídy** na pravé straně. Pojmenujte novou `IBookService` třídu a klikněte na **OK**.  
  
2. V horní části okna kódu, které se zobrazí, přidejte příkaz using do `System.Servicemodel`.  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3. Změňte definici ukázkové třídy na následující definici rozhraní.  
  
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
  
4. Sestavte projekt stisknutím **kombinace kláves CTRL + SHIFT + B**.  
  
### <a name="importing-the-service-contract"></a>Import kontraktu služby  
  
1. Klikněte pravým tlačítkem na projekt v **Průzkumník řešení** a vyberte **importovat kontrakt služby**. V části  **\<aktuální > projektu**otevřete všechny dílčí uzly a vyberte **IBookService**. Klikněte na **OK**.  
  
2. Otevře se dialogové okno s upozorněním, že operace byla úspěšně dokončena a že generované aktivity budou zobrazeny v sadě nástrojů po sestavení projektu. Klikněte na **OK**.  
  
3. Sestavte projekt stisknutím **kombinace kláves CTRL + SHIFT + B**, aby se importované aktivity zobrazily v sadě nástrojů.  
  
4. V **Průzkumník řešení**otevřete Service1. xamlx. Služba pracovního postupu se zobrazí v návrháři.  
  
5. Vyberte aktivitu **sekvence** . V okno Vlastnosti klikněte na **...** na tlačítko vlastnosti **implementedContract** . V okně **editoru kolekce typů** , které se zobrazí, klikněte na rozevírací seznam **typ** a vyberte možnost **Vyhledat typy...** uvedení. V dialogovém okně **Procházet a vybrat typ .NET** v části  **\<aktuální projekt >** otevřete všechny dílčí uzly a vyberte **IBookService**. Klikněte na **OK**. V dialogu **Editor kolekcí typů** klikněte na tlačítko **OK**.  
  
6. Vyberte a odstraňte aktivity **ReceiveRequest** a **SendResponse** .  
  
7. Z panelu nástrojů přetáhněte aktivitu **Buy_ReceiveAndSendReply** a **Checkout_Receive** na aktivitu **sekvenční služby** .
