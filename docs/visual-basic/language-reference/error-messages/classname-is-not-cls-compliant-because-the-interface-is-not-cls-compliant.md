---
title: '&#39;&lt;Název třídy&gt; &#39; není kompatibilní se specifikací CLS, protože rozhraní &#39; &lt;interfacename&gt; &#39; se implementuje není kompatibilní se specifikací CLS'
ms.date: 07/20/2015
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
ms.openlocfilehash: 4dda0e16a94f43cdb3deeff16fabdd1b10b62526
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588491"
---
# <a name="39ltclassnamegt39-is-not-cls-compliant-because-the-interface-39ltinterfacenamegt39-it-implements-is-not-cls-compliant"></a><span data-ttu-id="f8a72-102">&#39;&lt;Název třídy&gt; &#39; není kompatibilní se specifikací CLS, protože rozhraní &#39; &lt;interfacename&gt; &#39; se implementuje není kompatibilní se specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="f8a72-102">&#39;&lt;classname&gt;&#39; is not CLS-compliant because the interface &#39;&lt;interfacename&gt;&#39; it implements is not CLS-compliant</span></span>
<span data-ttu-id="f8a72-103">Třídy nebo rozhraní je označena jako `<CLSCompliant(True)>` , pokud je odvozena z nebo implementuje typ, který je označen jako `<CLSCompliant(False)>` nebo není označen.</span><span class="sxs-lookup"><span data-stu-id="f8a72-103">A class or interface is marked as `<CLSCompliant(True)>` when it derives from or implements a type that is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="f8a72-104">Pro třídy nebo rozhraní splňovat [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), jeho hierarchie dědičnosti celý musí splňovat předpisy.</span><span class="sxs-lookup"><span data-stu-id="f8a72-104">For a class or interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), its entire inheritance hierarchy must be compliant.</span></span> <span data-ttu-id="f8a72-105">To znamená, že každý typ, ze kterého se dědí, přímo ani nepřímo, musí být v souladu.</span><span class="sxs-lookup"><span data-stu-id="f8a72-105">That means every type from which it inherits, directly or indirectly, must be compliant.</span></span> <span data-ttu-id="f8a72-106">Podobně pokud třída implementuje jedno nebo více rozhraní, se musí být kompatibilní s v rámci své hierarchie dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="f8a72-106">Similarly, if a class implements one or more interfaces, they must all be compliant throughout their inheritance hierarchies.</span></span>  
  
 <span data-ttu-id="f8a72-107">Pokud použijete <xref:System.CLSCompliantAttribute> programovací element, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` indikující dodržování předpisů nebo nesplňujících požadavky.</span><span class="sxs-lookup"><span data-stu-id="f8a72-107">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="f8a72-108">Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f8a72-108">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="f8a72-109">Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, je považován za nedodržuje předpisy.</span><span class="sxs-lookup"><span data-stu-id="f8a72-109">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="f8a72-110">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="f8a72-110">By default, this message is a warning.</span></span> <span data-ttu-id="f8a72-111">Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="f8a72-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="f8a72-112">**ID chyby:** BC40029</span><span class="sxs-lookup"><span data-stu-id="f8a72-112">**Error ID:** BC40029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f8a72-113">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="f8a72-113">To correct this error</span></span>  
  
-   <span data-ttu-id="f8a72-114">Pokud budete potřebovat souladu se specifikací CLS, zadejte tento typ v jiné hierarchii nebo implementace schéma dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="f8a72-114">If you require CLS compliance, define this type within a different inheritance hierarchy or implementation scheme.</span></span>  
  
-   <span data-ttu-id="f8a72-115">Pokud požadujete, aby tento typ zůstávají ve své aktuální schéma hierarchie nebo implementace dědičnosti, odeberte <xref:System.CLSCompliantAttribute> z jeho definice nebo označte ji jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="f8a72-115">If you require that this type remain within its current inheritance hierarchy or implementation scheme, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
 
