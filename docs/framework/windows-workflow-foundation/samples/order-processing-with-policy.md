---
title: Zpracování objednávky pomocí zásad
ms.date: 03/30/2017
ms.assetid: 66833724-dc36-4fad-86b0-59ffeaa3ba6a
ms.openlocfilehash: b927d8e7090f96b22c0510f9651070ab999c91be
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398367"
---
# <a name="order-processing-with-policy"></a>Zpracování objednávky pomocí zásad
Pořadí zpracování zásad příklad ukazuje některé klíčové funkce [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Windows Workflow Foundation (WF). Následující funkce jsou nové pro stroj pravidel pracovního postupu:  
  
-   Podpora pro přetížení operátoru.  
  
-   Podpora `new` operátor umožňuje uživatelům vytvářet nové objekty a pole z pracovního postupu pravidla.  
  
-   Podpora pro rozšiřující metody uživatelského prostředí ve volání metody rozšíření z pravidla WF kompatibilní s stylů kódování C#.  
  
> [!NOTE]
>  Tato ukázka vyžaduje, aby [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] je nainstalovaná sestavení a spuštění. [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] je potřeba otevřít soubory projektu a řešení.  
  
 Ukázce `OrderProcessingPolicy` objednávku zákazníka, který se skládá z číslovaný seznam dostupných položek a PSČ, je zadaný projekt. Pořadí je úspěšně zpracovat, pokud obě položky jsou správná. jinak zásady vytvoří objekty chyba, využitím přetížený `+` operátor a předdefinované rozšiřující metoda uživatel informován o chybách.  
  
> [!NOTE]
>  Další informace o metodách rozšíření naleznete v tématu [3.0 specifikace verze jazyka C#](https://go.microsoft.com/fwlink/?LinkId=95402).  
  
 Ukázka se skládá z následující projekty:  
  
-   `OrderErrorLibrary`  
  
     `OrderErrorLibrary` Je knihovny tříd, který definuje `OrderError` a `OrderErrorCollection` třídy. `OrderError` Je vytvořena instance, pokud je zadán neplatný vstup. Knihovna také poskytuje metodu rozšíření na `OrderErrorCollection` třídy, jejichž výstupem jsou `ErrorText` vlastnost na všech `OrderError` objekty v `OrderErrorCollection`.  
  
-   `OrderProcessingPolicy`  
  
     `OrderProcessingPolicy` Projekt je konzolová aplikace pracovního postupu, který definuje jedinou `PolicyFromFile` aktivity. Aktivita má následující pravidla:  
  
    -   `invalidItemNum`  
  
         Toto pravidlo ověří, že je číslo mezi 1 a 6, včetně. Pokud je položka číslo v platném rozsahu, pravidlo nemá žádný účinek, (jiné než tisk do konzoly). Pokud není položka číslo mezi 1 a 6, `invalidItemNum` pravidlo provede následující:  
  
        1.  Vytvoří novou `OrderError` objektu, předají se jí číslo zadali a nastaví `ErrorText` a `CustomerName` vlastnosti objektu.  
  
        2.  Vytvoří `invalidItemNumErrorCollection` objektu.  
  
        3.  Přidá nově vytvořené `OrderError` instance na `invalidItemNumErrorCollection`.  
  
         Tento příklad ukazuje podporu `new` operátoru, pomocí kterého můžete vytvořit instanci objektů uvnitř pravidla.  
  
    -   `invalidZip`  
  
         Toto pravidlo ověří, že má 5 číslic PSČ a je v rozsahu 600 k 99998. Pokud je kód zip v platném rozsahu, pravidlo nemá žádný účinek, (jiné než tisk do konzoly). Pokud aplikace PSČ je menší než 5 nebo PSČ není mezi 00600 a 99998, `invalidZip` pravidlo provede následující:  
  
        1.  Vytvoří `OrderError` objektu, předají se jí zadán, PSČ a nastaví `ErrorText` a `CustomerName` vlastnosti objektu.  
  
        2.  Vytvoří `invalidZipCodeErrorCollection` objektu.  
  
        3.  Přidá nově vytvořené `OrderError` instance do nově vytvořené `invalidZipCodeErrorCollection`.  
  
         Toto pravidlo znovu ukazuje podporu `new` operátor, který umožňuje vytvořit instanci objektů uvnitř pravidla.  
  
    -   `displayErrors`  
  
         Toto pravidlo zkontroluje, pokud byly nějaké chyby přidal předchozí dvě pravidla ve dvou `OrderErrorCollection` objekty `invalidItemNumErrorCollection` a `invalidIZipCodeErrorCollection`. Pokud došlo k chybám (buď `invalidItemNumErrorCollection` nebo `invalidZipCodeErrorCollection` není `null`), pravidla provede následující akce:  
  
        1.  Volání přetížené `+` operátor zkopírujte obsah `invalidItemNumErrorCollection` a `invalidZipCodeErrorCollection` do `invalidOrdersCollection``OrderErrorCollection` instance.  
  
        2.  Volání `PrintOrderErrors` rozšiřující metody na `invalidOrdersCollection` a vypíše `ErrorText` vlastnost na všech `orderError` objekty v `invalidOrdersCollection`.  
  
 Přetížený operátor `+` na `OrderErrorCollection` je definována v `OrderErrorCollection` třídy v `OrderErrorLibrary` projektu. Má dva `OrderErrorCollection` objekty a kombinuje je do jedné `OrderErrorCollection` objektu.  
  
 `PrintOrderErrors` – Metoda rozšíření je také definováno v `OrderErrorLibrary` projektu. Rozšiřující metody jsou novou C# funkci, která vývojářům umožňuje přidat nové metody do veřejného kontraktu existujícího typu CLR, aniž byste museli odvodit třídu z něj nebo znovu zkompilovat původního typu.  
  
 Při spuštění ukázky budete vyzváni k zadání názvu, číslo položky položky, která se dá zakoupit a PSČ. Tyto informace potom ověřují z pravidel definovaných v rámci aktivity zásad. Tady je ukázkový výstup z programu.  
  
```  
Please enter your name: John  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 1  
  
Please enter your 5-Digit zip code: 98102  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Thank you for your order, it has been processed.  
  
Workflow Completed  
Another Order? (Y/N): y  
  
Please enter your name: Joel  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 8  
  
Please enter your 5-Digit zip code: 0000  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Your order contains the following error(s)  
  
Error: No item number found. Please choose an available item.  
Error: Invalid zip code. Please choose a zip code between 00600 and 99998.  
  
Workflow Completed  
Another Order? (Y/N): n  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Otevřete soubor projektu OrderProcessingPolicy.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Existují dva různé projekty v řešení: `OrderErrorLibrary` a `OrderProcessingPolicy`. `OrderProcessingPolicy` Projekt používá třídy a metody definované v `OrderErrorLibrary`.  
  
3.  Sestavte všechny projekty.  
  
4.  Klikněte na tlačítko **spustit**.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\OrderProcessingPolicy`