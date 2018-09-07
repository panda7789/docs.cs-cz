---
title: 'Postupy: Nahrazení rezervace adresy URL služby WCF omezenou rezervací'
ms.date: 03/30/2017
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
ms.openlocfilehash: b53596d7ac4e7e7c3748f6a98130492a96c0b48c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44059479"
---
# <a name="how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation"></a>Postupy: Nahrazení rezervace adresy URL služby WCF omezenou rezervací
Rezervace adresy URL můžete tak omezit, kdo přijímá zprávy z adresy URL nebo sadu adresy URL. Rezervace se skládá z adresy URL šablony, seznam řízení přístupu (ACL) a sada příznaků. Adresa URL Šablona definuje adresy URL, které má vliv na rezervaci. Další informace o způsobu zpracování adresy URL šablony najdete v tématu [směrování příchozích požadavků](https://go.microsoft.com/fwlink/?LinkId=136764). Seznam ACL ovládací prvky, které uživatel nebo skupina uživatelů je povolené pro příjem zpráv ze zadané adresy URL. Příznaky označí, zda je rezervace poskytnout oprávnění uživatele nebo skupinu tak, aby naslouchala na adresu URL přímo, nebo chcete delegovat oprávnění tak, aby naslouchala na nějaký jiný proces.  
  
 Jako součást výchozí konfigurace operačního systému Windows Communication Foundation (WCF) vytvoří globálně dostupné rezervace pro port 80 povolit všem uživatelům spouštět aplikace, které používají duální vazbu HTTP pro duplexní komunikaci. Vzhledem k tomu seznamu řízení přístupu na tuto rezervaci pro každého, správce nemůže explicitně povolte nebo zakažte oprávnění naslouchat na adresu URL nebo sadu adresy URL. Toto téma vysvětluje, jak odstranit tuto rezervaci a znovu vytvořit rezervaci s omezeným seznamu ACL.  
  
 Na [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo [!INCLUDE[lserver](../../../../includes/lserver-md.md)] můžete zobrazit všechny rezervace adresy URL protokolu HTTP z příkazového řádku se zvýšenými oprávněními zadejte `netsh http show urlacl`.  Následující příklad ukazuje, co by se mělo podobat rezervaci adresy URL WCF.  
  
```  
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```  
  
 Rezervace se skládá z adresy URL šablony aplikace WCF je používání duální vazbu HTTP pro duplexní komunikaci. Adresy URL tento formát se používají pro služby WCF k odesílání zpráv zpět do klienta WCF při komunikaci přes duální vazbu protokolu HTTP. Všichni uděleno oprávnění k naslouchání na adrese URL, ale nechcete delegovat na jiný proces. Nakonec seznamu ACL je popsán v zabezpečení popisovač Definition Language (SSDL). Další informace o SSDL, naleznete v tématu [SSDL](https://go.microsoft.com/fwlink/?LinkId=136789)  
  
### <a name="to-delete-the-wcf-url-reservation"></a>Chcete-li odstranit rezervaci adresy URL WCF  
  
1.  Klikněte na tlačítko **Start**, přejděte na **všechny programy**, klikněte na tlačítko **Příslušenství**, klikněte pravým tlačítkem na **příkazového řádku** a klikněte na tlačítko **spustit jako Správce** v místní nabídce, která se zobrazí. Klikněte na tlačítko **pokračovat** v okně Řízení uživatelských účtů (UAC), které může požádat o oprávnění, abyste mohli pokračovat.  
  
2.  Zadejte **netsh http delete urlacl url =http://+:80/Temporary_Listen_Addresses/**  v okně příkazového řádku.  
  
3.  Pokud rezervaci byl úspěšně odstraněn, zobrazí se následující zpráva. **Rezervace adresy URL se úspěšně odstranil**  
  
## <a name="creating-a-new-security-group-and-new-restricted-url-reservation"></a>Vytvoření nové skupiny zabezpečení a novou rezervaci adresy URL s omezeným přístupem  
 K nahrazení rezervace adresy URL WCF omezenou rezervací musíte nejprve vytvořit novou skupinu zabezpečení. Provedete to jedním ze dvou způsobů: z příkazového řádku nebo z konzoly Správa počítače. Stačí jedno.  
  
#### <a name="to-create-a-new-security-group-from-a-command-prompt"></a>Chcete-li vytvořit novou skupinu zabezpečení z příkazového řádku  
  
1.  Klikněte na tlačítko **Start**, přejděte na **všechny programy**, klikněte na tlačítko **Příslušenství**, klikněte pravým tlačítkem na **příkazového řádku** a klikněte na tlačítko **spustit jako Správce** v místní nabídce, která se zobrazí. Klikněte na tlačítko **pokračovat** v okně Řízení uživatelských účtů (UAC), které může požádat o oprávnění, abyste mohli pokračovat.  
  
2.  Zadejte **net localgroup "\<zabezpečení skupiny název >" / komentáře: "\<popis skupiny zabezpečení >" / add** příkazového řádku. Nahrazení  **\<název skupiny zabezpečení >** s názvem skupiny zabezpečení, kterou chcete vytvořit a  **\<popis skupiny zabezpečení >** s vhodnou popis Skupina zabezpečení.  
  
3.  Pokud skupinu zabezpečení proběhne úspěšně, zobrazí se následující zpráva. **Příkaz byl úspěšně dokončen.**  
  
#### <a name="to-create-a-new-security-group-from-the-computer-management-console"></a>Chcete-li vytvořit novou skupinu zabezpečení z konzoly Správa počítače  
  
1.  Klikněte na tlačítko **Start**, klikněte na tlačítko **ovládací panely**, klikněte na tlačítko **nástroje pro správu**a klikněte na tlačítko **Správa počítače** otevřete počítači Konzola pro správu. Klikněte na tlačítko **pokračovat** v okně Řízení uživatelských účtů (UAC), které může požádat o oprávnění, abyste mohli pokračovat.  
  
2.  Klikněte na tlačítko **systémové nástroje**, klikněte na tlačítko **místní uživatelé a skupiny**, klikněte pravým tlačítkem na **skupiny** složky a klikněte na tlačítko **nová skupina** v místní nabídce, která se zobrazí. Zadejte požadovaný **název skupiny**, **popis** a další podrobnosti o této nové skupiny zabezpečení a klikněte na tlačítko **vytvořit** pro vytvoření skupiny zabezpečení.  
  
#### <a name="to-create-the-restricted-url-reservation"></a>Chcete-li vytvořit s omezeným přístupem rezervaci adresy URL  
  
1.  Klikněte na tlačítko **Start**, přejděte na **všechny programy**, klikněte na tlačítko **Příslušenství**, klikněte pravým tlačítkem na **příkazového řádku** a klikněte na tlačítko **spustit jako Správce** v místní nabídce, která se zobrazí. Klikněte na tlačítko **pokračovat** v okně Řízení uživatelských účtů (UAC), které může požádat o oprávnění, abyste mohli pokračovat.  
  
2.  Zadejte **netsh http přidat adresu url urlacl =http://+:80/Temporary_Listen_Addresses/ uživatel = "\<název počítače >\\< název skupiny zabezpečení\>**  příkazového řádku. Nahrazení  **\<název počítače >** s názvem počítače, na kterém skupina musí být vytvořená a  **\<název skupiny zabezpečení >** s názvem skupinu zabezpečení, kterou jste vytvořili dříve.  
  
3.  Pokud rezervaci proběhne úspěšně, zobrazí se následující zpráva. **Rezervace adresy URL se úspěšně přidal**.
