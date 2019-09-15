---
title: 'Postupy: Nahrazení rezervace adresy URL služby WCF omezenou rezervací'
ms.date: 03/30/2017
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
ms.openlocfilehash: 981c4890b11130b937e176da78f378340c0d3894
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991665"
---
# <a name="how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation"></a>Postupy: Nahrazení rezervace adresy URL služby WCF omezenou rezervací
Rezervace adresy URL umožňuje omezit, kdo může přijímat zprávy z adresy URL nebo ze sady adres URL. Rezervace se skládá ze šablony adresy URL, seznamu řízení přístupu (ACL) a sady příznaků. Šablona adresy URL definuje adresy URL, které rezervace ovlivňuje. Další informace o tom, jak se zpracovávají šablony adres URL, najdete v tématu [směrování příchozích požadavků](https://go.microsoft.com/fwlink/?LinkId=136764). Seznam řízení přístupu (ACL) určuje, kteří uživatelé nebo skupiny uživatelů mají povolený příjem zpráv ze zadaných adres URL. Příznaky označují, zda má rezervace poskytnout uživateli nebo skupině oprávnění k naslouchání na adrese URL přímo nebo k delegování oprávnění k naslouchání jinému procesu.  
  
 V rámci výchozí konfigurace operačního systému vytvoří Windows Communication Foundation (WCF) globálně dostupnou rezervaci pro port 80, aby všichni uživatelé mohli spouštět aplikace, které pro duplexní komunikaci používají duální vazby HTTP. Vzhledem k tomu, že seznam ACL u této rezervace je pro všechny, správci nemůžou explicitně povolit nebo zakázat oprávnění k naslouchání na adrese URL nebo sadě adres URL. Toto téma vysvětluje, jak odstranit tuto rezervaci a jak znovu vytvořit rezervaci s omezeným seznamem ACL.  
  
 Můžete [!INCLUDE[wv](../../../../includes/wv-md.md)] `netsh http show urlacl`také [!INCLUDE[lserver](../../../../includes/lserver-md.md)] Zobrazit všechny rezervace adres URL protokolu HTTP z příkazového řádku se zvýšenými oprávněními zadáním.  Následující příklad ukazuje, co se má podobat rezervaci adresy URL WCF.  

```
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```

 Rezervace se skládá z šablony URL, která se používá, když aplikace WCF používá pro duplexní komunikaci Dual-Binding HTTP. Adresy URL tohoto formuláře se používají pro službu WCF k posílání zpráv zpátky klientovi WCF při komunikaci přes Dual-Binding HTTP. Každému uživateli je uděleno oprávnění k naslouchání na adrese URL, ale ne k delegování naslouchání dalšímu procesu. Seznam řízení přístupu (ACL) je popsán v tématu Security Descriptor Definition Language (SSDL). Další informace o SSDL najdete v tématu [SSDL](https://go.microsoft.com/fwlink/?LinkId=136789)  
  
## <a name="to-delete-the-wcf-url-reservation"></a>Odstranění rezervace adresy URL WCF  
  
1. Klikněte **na Start**, přejděte na **všechny programy**, klikněte na **příslušenství**, klikněte pravým tlačítkem myši na **příkazový řádek** a v kontextové nabídce klikněte na **Spustit jako správce** . V okně Řízení uživatelských účtů (UAC) klikněte na **pokračovat** , které může vyžadovat oprávnění k pokračování.  
  
2. V okně příkazového řádku zadejte příkaz **Netsh http://+:80/Temporary_Listen_Addresses/ http Delete urlacl URL =** .  
  
3. Pokud se rezervace úspěšně odstraní, zobrazí se následující zpráva. **Rezervace adresy URL se úspěšně odstranila.**  
  
## <a name="creating-a-new-security-group-and-new-restricted-url-reservation"></a>Vytvoření nové skupiny zabezpečení a nové rezervace omezené adresy URL  
 Pokud chcete rezervaci adresy URL WCF nahradit omezenou rezervací, musíte nejdřív vytvořit novou skupinu zabezpečení. To lze provést jedním ze dvou způsobů: z příkazového řádku nebo z konzoly pro správu počítače. Stačí provést pouze jeden.  
  
### <a name="to-create-a-new-security-group-from-a-command-prompt"></a>Vytvoření nové skupiny zabezpečení z příkazového řádku  
  
1. Klikněte **na Start**, přejděte na **všechny programy**, klikněte na **příslušenství**, klikněte pravým tlačítkem myši na **příkazový řádek** a v kontextové nabídce klikněte na **Spustit jako správce** . V okně Řízení uživatelských účtů (UAC) klikněte na **pokračovat** , které může vyžadovat oprávnění k pokračování.  
  
2. Do příkazového řádku zadejte do pole **net Local\<Group název skupiny zabezpečení >\<"/comment:" Popis skupiny zabezpečení > "/Add** . Nahrazením  **\<názvu skupiny zabezpečení >** názvem skupiny zabezpečení, kterou chcete vytvořit, a  **\<popis skupiny zabezpečení >** s vhodným popisem pro skupinu zabezpečení.  
  
3. Pokud se skupina zabezpečení úspěšně vytvoří, zobrazí se následující zpráva. **Příkaz byl úspěšně dokončen.**  
  
### <a name="to-create-a-new-security-group-from-the-computer-management-console"></a>Vytvoření nové skupiny zabezpečení z konzoly pro správu počítače  
  
1. Klikněte na tlačítko **Start**, klikněte na položku **Ovládací panely**, klikněte na položku **Nástroje pro správu**a otevřete konzolu Správa počítače kliknutím na položku **Správa počítače** . V okně Řízení uživatelských účtů (UAC) klikněte na **pokračovat** , které může vyžadovat oprávnění k pokračování.  
  
2. Klikněte na položku **Systémové nástroje**, klikněte na položku **místní uživatelé a skupiny**, klikněte pravým tlačítkem myši na položku **skupiny** a v místní nabídce klikněte na možnost **Nová skupina** . Zadejte požadovaný **název skupiny**, **Popis** a další podrobnosti této nové skupiny zabezpečení a kliknutím na tlačítko **vytvořit** vytvořte skupinu zabezpečení.  
  
### <a name="to-create-the-restricted-url-reservation"></a>Postup vytvoření rezervace adresy URL s omezeným přístupem  
  
1. Klikněte **na Start**, přejděte na **všechny programy**, klikněte na **příslušenství**, klikněte pravým tlačítkem myši na **příkazový řádek** a v kontextové nabídce klikněte na **Spustit jako správce** . V okně Řízení uživatelských účtů (UAC) klikněte na **pokračovat** , které může vyžadovat oprávnění k pokračování.  
  
2. Do příkazového řádku zadejte příkaz **netsh http http://+:80/Temporary_Listen_Addresses/ Add urlacl URL\< = User =\\"název počítače >\> < název skupiny zabezpečení** . Nahraďte  **\<název počítače >** názvem počítače, na kterém se skupina musí vytvořit, a  **\<názvem skupiny zabezpečení >** názvem skupiny zabezpečení, kterou jste předtím vytvořili.  
  
3. Je-li rezervace vytvořena úspěšně, zobrazí se následující zpráva. **Rezervace adresy URL se úspěšně přidala**.
