---
title: "Postupy: Nahrazení rezervace adresy URL služby WCF omezenou rezervací"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9dd631f08f9367576adf97f9139348bfce69a92f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation"></a>Postupy: Nahrazení rezervace adresy URL služby WCF omezenou rezervací
Rezervaci adresy URL můžete omezit, kdo může přijímat zprávy z adresy URL nebo sadu adres URL. Rezervace se skládá z šablony adresu URL, seznam řízení přístupu (ACL) a sadu příznaků. Adresa URL Šablona definuje adresy URL, které ovlivňuje rezervace. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]jak se zpracovávají šablony adresu URL, najdete v části [směrování příchozích požadavků](http://go.microsoft.com/fwlink/?LinkId=136764). Seznam řízení přístupu řídí, jaké uživatel nebo skupina uživatelů je povoleno přijímat zprávy ze zadaných adres URL. V příznacích označuje, zda rezervace udělit oprávnění uživatele nebo skupinu tak, aby naslouchala na adresu URL přímo, nebo chcete delegovat oprávnění pro naslouchání na jiný proces.  
  
 Jako součást výchozí konfigurace operačního systému [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vytvoří rezervace globálně přístupné pro port 80 povolit všem uživatelům spouštět aplikace, které používají duální vazby HTTP pro duplexní komunikace. Vzhledem k tomu, že seznam řízení přístupu na tuto rezervaci je pro všechny uživatele, správci nelze explicitně povolí nebo zakáže oprávnění tak, aby naslouchala na adresu URL nebo sadu adres URL. Toto téma vysvětluje, jak odstranit tuto rezervaci a jak znovu vytvořit rezervaci s seznam ACL pro s omezeným přístupem.  
  
 Na [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo [!INCLUDE[lserver](../../../../includes/lserver-md.md)] můžete zobrazit všechny rezervace adresy URL protokolu HTTP z příkazového řádku se zvýšenými oprávněními zadáním `netsh http show urlacl`.  Následující příklad ukazuje, jaké [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] by měla vypadat přibližně rezervaci adresy URL.  
  
```  
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```  
  
 Rezervace se skládá z adresy URL použije šablona, kdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace používá dva vazbu HTTP pro duplexní komunikace. Adresy URL tento formulář slouží k [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] službu pro odeslání zprávy zpět do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta při komunikaci přes duální vazbu protokolu HTTP. Všichni uděleno oprávnění tak, aby naslouchala na adresu URL, ale ne na delegovat naslouchání jiný proces. Nakonec seznamu ACL je popsána v zabezpečení popisovač Definition Language (SSDL). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]SSDL, najdete v části [SSDL](http://go.microsoft.com/fwlink/?LinkId=136789)  
  
### <a name="to-delete-the-wcf-url-reservation"></a>Odstranit rezervaci adresy URL WCF  
  
1.  Klikněte na tlačítko **spustit**, přejděte na příkaz **všechny programy**, klikněte na tlačítko **Příslušenství**, klikněte pravým tlačítkem na **příkazového řádku** a klikněte na tlačítko **spustit jako Správce** v místní nabídce, který se zobrazí. Klikněte na tlačítko **pokračovat** v okně Řízení uživatelských účtů (UAC), které vás může požádat oprávnění pokračujte.  
  
2.  Zadejte **netsh http odstranit urlacl url = http: / / +:80/Temporary_Listen_Addresses/** v okně příkazového řádku.  
  
3.  Pokud rezervace byla úspěšně odstraněna, zobrazí se následující zpráva. **Rezervaci adresy URL se úspěšně odstranil**  
  
## <a name="creating-a-new-security-group-and-new-restricted-url-reservation"></a>Vytvoření nové skupiny zabezpečení a novou rezervaci adresy URL s omezeným přístupem  
 Chcete-li nahradit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rezervaci adresy URL omezenou rezervací musí nejprve vytvoříte novou skupinu zabezpečení. Provedete to jedním ze dvou způsobů: z příkazového řádku nebo z konzoly Správa počítače. Můžete mít pouze pro jednu.  
  
#### <a name="to-create-a-new-security-group-from-a-command-prompt"></a>Chcete-li vytvořit novou skupinu zabezpečení z příkazového řádku  
  
1.  Klikněte na tlačítko **spustit**, přejděte na příkaz **všechny programy**, klikněte na tlačítko **Příslušenství**, klikněte pravým tlačítkem na **příkazového řádku** a klikněte na tlačítko **spustit jako Správce** v místní nabídce, který se zobrazí. Klikněte na tlačítko **pokračovat** v okně Řízení uživatelských účtů (UAC), které vás může požádat oprávnění pokračujte.  
  
2.  Zadejte **net localgroup "\<název skupiny zabezpečení >" / comment: "\<popis skupiny zabezpečení >" / add** na příkazovém řádku. Nahrazení  **\<název skupiny zabezpečení >** s názvem skupiny zabezpečení, kterou chcete vytvořit a  **\<popis skupiny zabezpečení >** s vhodný popis Skupina zabezpečení.  
  
3.  Pokud skupina zabezpečení se úspěšně vytvořil, zobrazí se následující zpráva. **Příkaz úspěšně dokončil.**  
  
#### <a name="to-create-a-new-security-group-from-the-computer-management-console"></a>Chcete-li vytvořit novou skupinu zabezpečení z konzoly Správa počítače  
  
1.  Klikněte na tlačítko **spustit**, klikněte na tlačítko **ovládací panely**, klikněte na tlačítko **nástroje pro správu**a klikněte na tlačítko **Správa počítače** otevřete počítače Konzola pro správu. Klikněte na tlačítko **pokračovat** v okně Řízení uživatelských účtů (UAC), které vás může požádat oprávnění pokračujte.  
  
2.  Klikněte na tlačítko **systémové nástroje**, klikněte na tlačítko **místní uživatelé a skupiny**, klikněte pravým tlačítkem na **skupiny** složky a klikněte na tlačítko **nová skupina** v místní nabídce, zobrazení. Zadejte požadovanou **název skupiny**, **popis** a další podrobnosti o této nové skupiny zabezpečení a klikněte na tlačítko **vytvořit** tlačítko pro vytvoření skupiny zabezpečení.  
  
#### <a name="to-create-the-restricted-url-reservation"></a>Chcete-li vytvořit rezervaci adresy URL s omezeným přístupem  
  
1.  Klikněte na tlačítko **spustit**, přejděte na příkaz **všechny programy**, klikněte na tlačítko **Příslušenství**, klikněte pravým tlačítkem na **příkazového řádku** a klikněte na tlačítko **spustit jako Správce** v místní nabídce, který se zobrazí. Klikněte na tlačítko **pokračovat** v okně Řízení uživatelských účtů (UAC), které vás může požádat oprávnění pokračujte.  
  
2.  Zadejte **netsh http přidejte adresu url urlacl = http: / / +: 80/Temporary_Listen_Addresses/uživatel = "\<název počítače >\\< název skupiny zabezpečení\>**  na příkazovém řádku. Nahrazení  **\<název počítače >** s názvem počítače, na kterém musí být skupina vytvořena a  **\<název skupiny zabezpečení >** s názvem skupiny zabezpečení, kterou jste vytvořili dříve.  
  
3.  Pokud rezervace byla úspěšně vytvořena, zobrazí se následující zpráva. **Rezervaci adresy URL úspěšně přidal**.
