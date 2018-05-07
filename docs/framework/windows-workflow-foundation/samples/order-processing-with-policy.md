---
title: Pořadí zpracování pomocí zásad
ms.date: 03/30/2017
ms.assetid: 66833724-dc36-4fad-86b0-59ffeaa3ba6a
ms.openlocfilehash: 15e274a7a513a3208e3a54575dc354310743b731
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="order-processing-with-policy"></a>Pořadí zpracování pomocí zásad
Příklad pořadí zpracování zásad ukazuje některé klíčové funkce byla zavedená v [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Windows Workflow Foundation (WF). Následující funkce jsou nové pro modul pravidla pracovního postupu:  
  
-   Podpora pro přetížení operátoru.  
  
-   Podpora pro `new` operátor, což umožňuje uživatelům vytvářet nové objekty a pole z pravidel WF.  
  
-   Podpora pro rozšíření metod, jak se uživateli při volání metody rozšíření z pravidel WF kompatibilní s kódování styly C#.  
  
> [!NOTE]
>  Tato ukázka vyžaduje, aby [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] je nainstalovaná pro sestavení a spuštění. [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] je potřeba otevřít soubory projektu a řešení.  
  
 Ukázka ukazuje `OrderProcessingPolicy` projektu v pořadí zákazníka, které se skládá z číslovaný seznam dostupné položky a PSČ, je zadána. Pořadí je úspěšně zpracovat, pokud jsou obě položky správné; jinak zásady vytvoří objekty chyby, využívá přetížené `+` operátor a metoda předdefinované rozšíření informovat uživatele chyby.  
  
> [!NOTE]
>  Další informace o metodách rozšíření najdete v tématu [C# verze 3.0 specifikace](http://go.microsoft.com/fwlink/?LinkId=95402).  
  
 Ukázka se skládá z následujících projektech:  
  
-   `OrderErrorLibrary`  
  
     `OrderErrorLibrary` Třída knihovnu, která definuje `OrderError` a `OrderErrorCollection` třídy. `OrderError` Instance se vytvoří, když je zadaný neplatný vstup. Knihovna také poskytuje metody rozšíření na `OrderErrorCollection` třídu, která výstupy `ErrorText` vlastnost na všech `OrderError` objekty v `OrderErrorCollection`.  
  
-   `OrderProcessingPolicy`  
  
     `OrderProcessingPolicy` Projekt je konzolová aplikace pracovního postupu, která definuje jeden `PolicyFromFile` aktivity. Aktivita má následující pravidla:  
  
    -   `invalidItemNum`  
  
         Toto pravidlo ověří, zda číslo položky je mezi 1 a 6 (včetně). Pokud je číslo položky v platném rozsahu, pravidlo se nic nestane. (jiné než tisk do konzoly). Pokud není číslo mezi 1 a 6, `invalidItemNum` pravidlo provede následující akce:  
  
        1.  Vytvoří novou `OrderError` objektu předání číslo zadali a nastaví `ErrorText` a `CustomerName` vlastnosti objektu.  
  
        2.  Vytvoří `invalidItemNumErrorCollection` objektu.  
  
        3.  Přidá nově vytvořené `OrderError` instance na `invalidItemNumErrorCollection`.  
  
         Tento příklad ukazuje, podpora `new` operátor, pomocí kterého můžete vytvořit instanci objekty uvnitř pravidla.  
  
    -   `invalidZip`  
  
         Toto pravidlo ověří, zda kód zip 5 číslic a je v rozsahu 600 k 99998. Pokud je kód zip v platném rozsahu, pravidlo se nic nestane. (jiné než tisk do konzoly). Pokud délka zadané PSČ je menší než 5 nebo kód zip není mezi 00600 a 99998, `invalidZip` pravidlo provede následující akce:  
  
        1.  Vytvoří `OrderError` objektu předání PSČ zadán a nastaví `ErrorText` a `CustomerName` vlastnosti objektu.  
  
        2.  Vytvoří `invalidZipCodeErrorCollection` objektu.  
  
        3.  Přidá nově vytvořené `OrderError` instance nově vytvořené `invalidZipCodeErrorCollection`.  
  
         Toto pravidlo znovu ukazuje podpora `new` operátor, který slouží k vytváření instancí objektů uvnitř pravidla.  
  
    -   `displayErrors`  
  
         Toto pravidlo zkontroluje, pokud došlo k chybám žádné přidal předchozí dvě pravidla ve dvou `OrderErrorCollection` objekty `invalidItemNumErrorCollection` a `invalidIZipCodeErrorCollection`. Pokud došlo k chybám (buď `invalidItemNumErrorCollection` nebo `invalidZipCodeErrorCollection` není `null`), pravidlo provede následující akce:  
  
        1.  Volání přetížené `+` operátor a zkopírujte obsah `invalidItemNumErrorCollection` a `invalidZipCodeErrorCollection` k `invalidOrdersCollection``OrderErrorCollection` instance.  
  
        2.  Volání `PrintOrderErrors` rozšiřující metody na `invalidOrdersCollection` a výstupy `ErrorText` vlastnost na všech `orderError` objekty v `invalidOrdersCollection`.  
  
 Přetížené operátor `+` na `OrderErrorCollection` je definována v `OrderErrorCollection` třídy v `OrderErrorLibrary` projektu. Dva trvá `OrderErrorCollection` objekty a sloučí je do jedné `OrderErrorCollection` objektu.  
  
 `PrintOrderErrors` Metoda rozšíření je také definován ve `OrderErrorLibrary` projektu. Rozšiřující metody jsou nová C# funkce, která vývojářům umožňuje přidat nové metody do veřejného kontraktu existujícího typu CLR, aniž by museli odvození třídy z něj nebo znovu zkompiluje původní typ.  
  
 Při spuštěním ukázky budete vyzváni k zadání názvu, číslo položky je možné zakoupit a kód zip. Tyto informace pak ověří pravidla definovaná v aktivity zásad. Zde je ukázkový výstup z programu.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Otevřete soubor projektu OrderProcessingPolicy.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Existují dva různé projekty v řešení: `OrderErrorLibrary` a `OrderProcessingPolicy`. `OrderProcessingPolicy` Projektu používá třídy a metody definované v `OrderErrorLibrary`.  
  
3.  Všechny projekty sestavení.  
  
4.  Klikněte na tlačítko **spustit**.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\OrderProcessingPolicy`