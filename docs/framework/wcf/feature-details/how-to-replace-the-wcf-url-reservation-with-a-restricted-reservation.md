---
title: 'Postupy: Nahrazení rezervace adresy URL služby WCF omezenou rezervací'
ms.date: 03/30/2017
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
ms.openlocfilehash: a7025636bb1ca2ef250d7d25634bda961f2db09d
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811610"
---
# <a name="how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation"></a>Postupy: Nahrazení rezervace adresy URL služby WCF omezenou rezervací

Rezervace adresy URL umožňuje omezit, kdo může přijímat zprávy z adresy URL nebo ze sady adres URL. Rezervace se skládá ze šablony adresy URL, seznamu řízení přístupu (ACL) a sady příznaků. Šablona adresy URL definuje adresy URL, které rezervace ovlivňuje. Další informace o tom, jak se zpracovávají šablony adres URL, najdete v tématu [směrování příchozích požadavků](/windows/win32/http/routing-incoming-requests). Seznam řízení přístupu (ACL) určuje, kteří uživatelé nebo skupiny uživatelů mají povolený příjem zpráv ze zadaných adres URL. Příznaky označují, zda má rezervace poskytnout uživateli nebo skupině oprávnění k naslouchání na adrese URL přímo nebo k delegování oprávnění k naslouchání jinému procesu.  
  
 V rámci výchozí konfigurace operačního systému vytvoří Windows Communication Foundation (WCF) globálně dostupnou rezervaci pro port 80, aby všichni uživatelé mohli spouštět aplikace, které pro duplexní komunikaci používají duální vazby HTTP. Vzhledem k tomu, že seznam ACL u této rezervace je pro všechny, správci nemůžou explicitně povolit nebo zakázat oprávnění k naslouchání na adrese URL nebo sadě adres URL. Toto téma vysvětluje, jak odstranit tuto rezervaci a jak znovu vytvořit rezervaci s omezeným seznamem ACL.  
  
V systému Windows Vista nebo Windows Server 2008 můžete zadáním příkazu Zobrazit všechny rezervace adres URL protokolu HTTP z příkazového řádku se zvýšenými oprávněními `netsh http show urlacl` . Následující příklad ukazuje, co se má podobat rezervaci adresy URL WCF:

```output
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```

 Rezervace se skládá z šablony URL, která se používá, když aplikace WCF používá pro duplexní komunikaci Dual-Binding HTTP. Adresy URL tohoto formuláře se používají pro službu WCF k posílání zpráv zpátky klientovi WCF při komunikaci přes Dual-Binding HTTP. Každému uživateli je uděleno oprávnění k naslouchání na adrese URL, ale ne k delegování naslouchání dalšímu procesu. Seznam řízení přístupu (ACL) je popsán v tématu Security Descriptor Definition Language (SSDL). Další informace o SSDL najdete v tématu [SSDL](/windows/win32/secauthz/security-descriptor-definition-language)  
  
## <a name="to-delete-the-wcf-url-reservation"></a>Odstranění rezervace adresy URL WCF  
  
1. Klikněte **na Start**, přejděte na **všechny programy**, klikněte na **příslušenství**, klikněte pravým tlačítkem myši na **příkazový řádek** a v kontextové nabídce klikněte na **Spustit jako správce** . V okně Řízení uživatelských účtů (UAC) klikněte na **pokračovat** , které může vyžadovat oprávnění k pokračování.  
  
2. V `netsh http delete urlacl url=http://+:80/Temporary_Listen_Addresses/` okně příkazového řádku zadejte.  
  
3. Pokud se rezervace úspěšně odstraní, zobrazí se následující zpráva. **Rezervace adresy URL se úspěšně odstranila.**  
  
## <a name="creating-a-new-security-group-and-new-restricted-url-reservation"></a>Vytvoření nové skupiny zabezpečení a nové rezervace omezené adresy URL  
 Pokud chcete rezervaci adresy URL WCF nahradit omezenou rezervací, musíte nejdřív vytvořit novou skupinu zabezpečení. To lze provést jedním ze dvou způsobů: z příkazového řádku nebo z konzoly pro správu počítače. Stačí provést pouze jeden.  
  
### <a name="to-create-a-new-security-group-from-a-command-prompt"></a>Vytvoření nové skupiny zabezpečení z příkazového řádku  
  
1. Klikněte **na Start**, přejděte na **všechny programy**, klikněte na **příslušenství**, klikněte pravým tlačítkem myši na **příkazový řádek** a v kontextové nabídce klikněte na **Spustit jako správce** . V okně Řízení uživatelských účtů (UAC) klikněte na **pokračovat** , které může vyžadovat oprávnění k pokračování.  
  
2. Do `net localgroup "<security group name>" /comment:"<security group description>" /add` příkazového řádku zadejte. Nahraďte **\<security group name>** názvem skupiny zabezpečení, kterou chcete vytvořit, a **\<security group description>** s vhodným popisem pro skupinu zabezpečení.  
  
3. Pokud se skupina zabezpečení úspěšně vytvoří, zobrazí se následující zpráva. **Příkaz byl úspěšně dokončen.**  
  
### <a name="to-create-a-new-security-group-from-the-computer-management-console"></a>Vytvoření nové skupiny zabezpečení z konzoly pro správu počítače  
  
1. Klikněte na tlačítko **Start**, klikněte na položku **Ovládací panely**, klikněte na položku **Nástroje pro správu**a otevřete konzolu Správa počítače kliknutím na položku **Správa počítače** . V okně Řízení uživatelských účtů (UAC) klikněte na **pokračovat** , které může vyžadovat oprávnění k pokračování.  
  
2. Klikněte na položku **Systémové nástroje**, klikněte na položku **místní uživatelé a skupiny**, klikněte pravým tlačítkem myši na položku **skupiny** a v místní nabídce klikněte na možnost **Nová skupina** . Zadejte požadovaný **název skupiny**, **Popis** a další podrobnosti této nové skupiny zabezpečení a kliknutím na tlačítko **vytvořit** vytvořte skupinu zabezpečení.  
  
### <a name="to-create-the-restricted-url-reservation"></a>Postup vytvoření rezervace adresy URL s omezeným přístupem  
  
1. Klikněte **na Start**, přejděte na **všechny programy**, klikněte na **příslušenství**, klikněte pravým tlačítkem myši na **příkazový řádek** a v kontextové nabídce klikněte na **Spustit jako správce** . V okně Řízení uživatelských účtů (UAC) klikněte na **pokračovat** , které může vyžadovat oprávnění k pokračování.  
  
2. Do `netsh http add urlacl url=http://+:80/Temporary_Listen_Addresses/ user="<machine name>\<security group name>` příkazového řádku zadejte. Nahraďte **\<machine name>** názvem počítače, na kterém se skupina musí vytvořit, a **\<security group name>** názvem skupiny zabezpečení, kterou jste předtím vytvořili.  
  
3. Je-li rezervace vytvořena úspěšně, zobrazí se následující zpráva. **Rezervace adresy URL se úspěšně přidala**.
