---
title: Název třídy '<classname> není kompatibilní se specifikací CLS, protože rozhraní '<interfacename>', které implementuje, není kompatibilní se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
ms.openlocfilehash: 063c42249abbfb506fd15311659599b4777d397f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975543"
---
# <a name="classname-is-not-cls-compliant-because-the-interface-interfacename-it-implements-is-not-cls-compliant"></a><span data-ttu-id="b55ec-102">"\<classname >' není kompatibilní se Specifikací CLS, protože rozhraní"\<interfacename > "ji implementuje, není kompatibilní se Specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="b55ec-102">'\<classname>' is not CLS-compliant because the interface '\<interfacename>' it implements is not CLS-compliant</span></span>
<span data-ttu-id="b55ec-103">Třídy nebo rozhraní je označen jako `<CLSCompliant(True)>` , pokud je odvozena od nebo implementuje typ, který je označen jako `<CLSCompliant(False)>` nebo není označen.</span><span class="sxs-lookup"><span data-stu-id="b55ec-103">A class or interface is marked as `<CLSCompliant(True)>` when it derives from or implements a type that is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="b55ec-104">Pro třídu nebo rozhraní, které má být zajištěn soulad [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), její hierarchie dědění celý musí splňovat předpisy.</span><span class="sxs-lookup"><span data-stu-id="b55ec-104">For a class or interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), its entire inheritance hierarchy must be compliant.</span></span> <span data-ttu-id="b55ec-105">To znamená, že každý typ, ze kterého se dědí, přímo nebo nepřímo, musí být kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="b55ec-105">That means every type from which it inherits, directly or indirectly, must be compliant.</span></span> <span data-ttu-id="b55ec-106">Podobně pokud třída implementuje jednu nebo více rozhraní, se musí být všechny předpisy v rámci své hierarchie dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="b55ec-106">Similarly, if a class implements one or more interfaces, they must all be compliant throughout their inheritance hierarchies.</span></span>  
  
 <span data-ttu-id="b55ec-107">Pokud použijete <xref:System.CLSCompliantAttribute> na programovací prvek, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` k označení dodržování předpisů nebo při nedodržení předpisů.</span><span class="sxs-lookup"><span data-stu-id="b55ec-107">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="b55ec-108">Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b55ec-108">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="b55ec-109">Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, se považuje za jako nevyhovující.</span><span class="sxs-lookup"><span data-stu-id="b55ec-109">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="b55ec-110">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="b55ec-110">By default, this message is a warning.</span></span> <span data-ttu-id="b55ec-111">Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b55ec-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="b55ec-112">**ID chyby:** BC40029</span><span class="sxs-lookup"><span data-stu-id="b55ec-112">**Error ID:** BC40029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b55ec-113">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b55ec-113">To correct this error</span></span>  
  
-   <span data-ttu-id="b55ec-114">Pokud budete vyžadovat dodržování specifikace CLS, definujte schéma hierarchie nebo k provádění různých dědičnosti tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="b55ec-114">If you require CLS compliance, define this type within a different inheritance hierarchy or implementation scheme.</span></span>  
  
-   <span data-ttu-id="b55ec-115">Pokud budete vyžadovat, že tento typ větší než doporučovaných její aktuální schéma hierarchie nebo implementace dědičnosti, odeberte <xref:System.CLSCompliantAttribute> z jeho definice nebo označte ji jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="b55ec-115">If you require that this type remain within its current inheritance hierarchy or implementation scheme, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
