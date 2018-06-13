---
title: Kolekce schématu rozhraní ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: 36d0859b897bfcea33803c219ade14722ed90421
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766644"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="1ac46-102">Kolekce schématu rozhraní ODBC</span><span class="sxs-lookup"><span data-stu-id="1ac46-102">ODBC Schema Collections</span></span>
<span data-ttu-id="1ac46-103">Tato část popisuje podporu kolekci schématu pro ovladače ODBC pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="1ac46-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="1ac46-104">Ovladač ODBC Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="1ac46-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="1ac46-105">Ovladač ODBC Microsoft SQL Server podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="1ac46-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="1ac46-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="1ac46-106">Tables</span></span>  
  
-   <span data-ttu-id="1ac46-107">Indexy</span><span class="sxs-lookup"><span data-stu-id="1ac46-107">Indexes</span></span>  
  
-   <span data-ttu-id="1ac46-108">Sloupce</span><span class="sxs-lookup"><span data-stu-id="1ac46-108">Columns</span></span>  
  
-   <span data-ttu-id="1ac46-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="1ac46-109">Procedures</span></span>  
  
-   <span data-ttu-id="1ac46-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="1ac46-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="1ac46-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="1ac46-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="1ac46-112">zobrazení</span><span class="sxs-lookup"><span data-stu-id="1ac46-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="1ac46-113">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="1ac46-113">Tables and Views</span></span>  
  
|<span data-ttu-id="1ac46-114">columnName</span><span class="sxs-lookup"><span data-stu-id="1ac46-114">ColumnName</span></span>|<span data-ttu-id="1ac46-115">Datový typ</span><span class="sxs-lookup"><span data-stu-id="1ac46-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1ac46-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="1ac46-116">TABLE_CAT</span></span>|<span data-ttu-id="1ac46-117">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-117">String</span></span>|  
|<span data-ttu-id="1ac46-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="1ac46-118">TABLE_SCHEM</span></span>|<span data-ttu-id="1ac46-119">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-119">String</span></span>|  
|<span data-ttu-id="1ac46-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-120">TABLE_NAME</span></span>|<span data-ttu-id="1ac46-121">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-121">String</span></span>|  
|<span data-ttu-id="1ac46-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-122">TABLE_TYPE</span></span>|<span data-ttu-id="1ac46-123">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-123">String</span></span>|  
|<span data-ttu-id="1ac46-124">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ac46-124">REMARKS</span></span>|<span data-ttu-id="1ac46-125">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="1ac46-126">Indexy</span><span class="sxs-lookup"><span data-stu-id="1ac46-126">Indexes</span></span>  
  
|<span data-ttu-id="1ac46-127">columnName</span><span class="sxs-lookup"><span data-stu-id="1ac46-127">ColumnName</span></span>|<span data-ttu-id="1ac46-128">Datový typ</span><span class="sxs-lookup"><span data-stu-id="1ac46-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1ac46-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="1ac46-129">TABLE_CAT</span></span>|<span data-ttu-id="1ac46-130">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-130">String</span></span>|  
|<span data-ttu-id="1ac46-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="1ac46-131">TABLE_SCHEM</span></span>|<span data-ttu-id="1ac46-132">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-132">String</span></span>|  
|<span data-ttu-id="1ac46-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-133">TABLE_NAME</span></span>|<span data-ttu-id="1ac46-134">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-134">String</span></span>|  
|<span data-ttu-id="1ac46-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="1ac46-135">NON_UNIQUE</span></span>|<span data-ttu-id="1ac46-136">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-136">Int16</span></span>|  
|<span data-ttu-id="1ac46-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="1ac46-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="1ac46-138">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-138">String</span></span>|  
|<span data-ttu-id="1ac46-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-139">INDEX_NAME</span></span>|<span data-ttu-id="1ac46-140">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-140">String</span></span>|  
|<span data-ttu-id="1ac46-141">TYP</span><span class="sxs-lookup"><span data-stu-id="1ac46-141">TYPE</span></span>|<span data-ttu-id="1ac46-142">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-142">Int16</span></span>|  
|<span data-ttu-id="1ac46-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1ac46-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="1ac46-144">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-144">Int16</span></span>|  
|<span data-ttu-id="1ac46-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-145">COLUMN_NAME</span></span>|<span data-ttu-id="1ac46-146">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-146">String</span></span>|  
|<span data-ttu-id="1ac46-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="1ac46-147">ASC_OR_DESC</span></span>|<span data-ttu-id="1ac46-148">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-148">String</span></span>|  
|<span data-ttu-id="1ac46-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="1ac46-149">CARDINATLITY</span></span>|<span data-ttu-id="1ac46-150">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-150">Int32</span></span>|  
|<span data-ttu-id="1ac46-151">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="1ac46-151">PAGES</span></span>|<span data-ttu-id="1ac46-152">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-152">Int32</span></span>|  
|<span data-ttu-id="1ac46-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="1ac46-153">FILTER_CONDITION</span></span>|<span data-ttu-id="1ac46-154">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-154">String</span></span>|  
|<span data-ttu-id="1ac46-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1ac46-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="1ac46-156">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-156">String</span></span>|  
|<span data-ttu-id="1ac46-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="1ac46-158">Byte</span><span class="sxs-lookup"><span data-stu-id="1ac46-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="1ac46-159">Sloupce</span><span class="sxs-lookup"><span data-stu-id="1ac46-159">Columns</span></span>  
  
|<span data-ttu-id="1ac46-160">columnName</span><span class="sxs-lookup"><span data-stu-id="1ac46-160">ColumnName</span></span>|<span data-ttu-id="1ac46-161">Datový typ</span><span class="sxs-lookup"><span data-stu-id="1ac46-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1ac46-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="1ac46-162">TABLE_CAT</span></span>|<span data-ttu-id="1ac46-163">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-163">String</span></span>|  
|<span data-ttu-id="1ac46-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="1ac46-164">TABLE_SCHEM</span></span>|<span data-ttu-id="1ac46-165">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-165">String</span></span>|  
|<span data-ttu-id="1ac46-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-166">TABLE_NAME</span></span>|<span data-ttu-id="1ac46-167">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-167">String</span></span>|  
|<span data-ttu-id="1ac46-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-168">COLUMN_NAME</span></span>|<span data-ttu-id="1ac46-169">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-169">String</span></span>|  
|<span data-ttu-id="1ac46-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-170">DATA_TYPE</span></span>|<span data-ttu-id="1ac46-171">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-171">Int16</span></span>|  
|<span data-ttu-id="1ac46-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-172">TYPE_NAME</span></span>|<span data-ttu-id="1ac46-173">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-173">String</span></span>|  
|<span data-ttu-id="1ac46-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="1ac46-174">COLUMN_SIZE</span></span>|<span data-ttu-id="1ac46-175">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-175">Int32</span></span>|  
|<span data-ttu-id="1ac46-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1ac46-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="1ac46-177">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-177">Int32</span></span>|  
|<span data-ttu-id="1ac46-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="1ac46-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="1ac46-179">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-179">Int16</span></span>|  
|<span data-ttu-id="1ac46-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="1ac46-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="1ac46-181">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-181">Int16</span></span>|  
|<span data-ttu-id="1ac46-182">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="1ac46-182">NULLABLE</span></span>|<span data-ttu-id="1ac46-183">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-183">Int16</span></span>|  
|<span data-ttu-id="1ac46-184">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ac46-184">REMARKS</span></span>|<span data-ttu-id="1ac46-185">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-185">String</span></span>|  
|<span data-ttu-id="1ac46-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="1ac46-186">COLUMN_DEF</span></span>|<span data-ttu-id="1ac46-187">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-187">String</span></span>|  
|<span data-ttu-id="1ac46-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="1ac46-189">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-189">Int16</span></span>|  
|<span data-ttu-id="1ac46-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="1ac46-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="1ac46-191">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-191">Int16</span></span>|  
|<span data-ttu-id="1ac46-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1ac46-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="1ac46-193">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-193">Int32</span></span>|  
|<span data-ttu-id="1ac46-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1ac46-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="1ac46-195">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-195">Int32</span></span>|  
|<span data-ttu-id="1ac46-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="1ac46-196">IS_NULLABLE</span></span>|<span data-ttu-id="1ac46-197">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-197">String</span></span>|  
|<span data-ttu-id="1ac46-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1ac46-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="1ac46-199">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-199">String</span></span>|  
|<span data-ttu-id="1ac46-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1ac46-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="1ac46-201">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-201">String</span></span>|  
|<span data-ttu-id="1ac46-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="1ac46-203">Byte</span><span class="sxs-lookup"><span data-stu-id="1ac46-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="1ac46-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="1ac46-204">Procedures</span></span>  
  
|<span data-ttu-id="1ac46-205">columnName</span><span class="sxs-lookup"><span data-stu-id="1ac46-205">ColumnName</span></span>|<span data-ttu-id="1ac46-206">Datový typ</span><span class="sxs-lookup"><span data-stu-id="1ac46-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1ac46-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="1ac46-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="1ac46-208">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-208">String</span></span>|  
|<span data-ttu-id="1ac46-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="1ac46-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="1ac46-210">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-210">String</span></span>|  
|<span data-ttu-id="1ac46-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="1ac46-212">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-212">String</span></span>|  
|<span data-ttu-id="1ac46-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="1ac46-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="1ac46-214">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-214">Int32</span></span>|  
|<span data-ttu-id="1ac46-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="1ac46-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="1ac46-216">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-216">Int32</span></span>|  
|<span data-ttu-id="1ac46-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="1ac46-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="1ac46-218">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-218">Int32</span></span>|  
|<span data-ttu-id="1ac46-219">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ac46-219">REMARKS</span></span>|<span data-ttu-id="1ac46-220">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-220">String</span></span>|  
|<span data-ttu-id="1ac46-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="1ac46-222">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="1ac46-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="1ac46-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="1ac46-224">columnName</span><span class="sxs-lookup"><span data-stu-id="1ac46-224">ColumnName</span></span>|<span data-ttu-id="1ac46-225">Datový typ</span><span class="sxs-lookup"><span data-stu-id="1ac46-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1ac46-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="1ac46-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="1ac46-227">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-227">String</span></span>|  
|<span data-ttu-id="1ac46-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="1ac46-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="1ac46-229">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-229">String</span></span>|  
|<span data-ttu-id="1ac46-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="1ac46-231">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-231">String</span></span>|  
|<span data-ttu-id="1ac46-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-232">COLUMN_NAME</span></span>|<span data-ttu-id="1ac46-233">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-233">String</span></span>|  
|<span data-ttu-id="1ac46-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-234">COLUMN_TYPE</span></span>|<span data-ttu-id="1ac46-235">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-235">Int16</span></span>|  
|<span data-ttu-id="1ac46-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-236">DATA_TYPE</span></span>|<span data-ttu-id="1ac46-237">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-237">Int16</span></span>|  
|<span data-ttu-id="1ac46-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-238">TYPE_NAME</span></span>|<span data-ttu-id="1ac46-239">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-239">String</span></span>|  
|<span data-ttu-id="1ac46-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="1ac46-240">COLUMN_SIZE</span></span>|<span data-ttu-id="1ac46-241">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-241">Int32</span></span>|  
|<span data-ttu-id="1ac46-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1ac46-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="1ac46-243">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-243">Int32</span></span>|  
|<span data-ttu-id="1ac46-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="1ac46-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="1ac46-245">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-245">Int16</span></span>|  
|<span data-ttu-id="1ac46-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="1ac46-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="1ac46-247">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-247">Int16</span></span>|  
|<span data-ttu-id="1ac46-248">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="1ac46-248">NULLABLE</span></span>|<span data-ttu-id="1ac46-249">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-249">Int16</span></span>|  
|<span data-ttu-id="1ac46-250">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ac46-250">REMARKS</span></span>|<span data-ttu-id="1ac46-251">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-251">String</span></span>|  
|<span data-ttu-id="1ac46-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="1ac46-252">COLUMN_DEF</span></span>|<span data-ttu-id="1ac46-253">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-253">String</span></span>|  
|<span data-ttu-id="1ac46-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="1ac46-255">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-255">Int16</span></span>|  
|<span data-ttu-id="1ac46-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="1ac46-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="1ac46-257">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-257">Int16</span></span>|  
|<span data-ttu-id="1ac46-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1ac46-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="1ac46-259">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-259">Int32</span></span>|  
|<span data-ttu-id="1ac46-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1ac46-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="1ac46-261">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-261">Int32</span></span>|  
|<span data-ttu-id="1ac46-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="1ac46-262">IS_NULLABLE</span></span>|<span data-ttu-id="1ac46-263">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-263">String</span></span>|  
|<span data-ttu-id="1ac46-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1ac46-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="1ac46-265">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-265">String</span></span>|  
|<span data-ttu-id="1ac46-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1ac46-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="1ac46-267">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-267">String</span></span>|  
|<span data-ttu-id="1ac46-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="1ac46-269">Byte</span><span class="sxs-lookup"><span data-stu-id="1ac46-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="1ac46-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="1ac46-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="1ac46-271">columnName</span><span class="sxs-lookup"><span data-stu-id="1ac46-271">ColumnName</span></span>|<span data-ttu-id="1ac46-272">Datový typ</span><span class="sxs-lookup"><span data-stu-id="1ac46-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1ac46-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="1ac46-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="1ac46-274">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-274">String</span></span>|  
|<span data-ttu-id="1ac46-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="1ac46-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="1ac46-276">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-276">String</span></span>|  
|<span data-ttu-id="1ac46-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="1ac46-278">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-278">String</span></span>|  
|<span data-ttu-id="1ac46-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-279">COLUMN_NAME</span></span>|<span data-ttu-id="1ac46-280">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-280">String</span></span>|  
|<span data-ttu-id="1ac46-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-281">COLUMN_TYPE</span></span>|<span data-ttu-id="1ac46-282">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-282">Int16</span></span>|  
|<span data-ttu-id="1ac46-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-283">DATA_TYPE</span></span>|<span data-ttu-id="1ac46-284">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-284">Int16</span></span>|  
|<span data-ttu-id="1ac46-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-285">TYPE_NAME</span></span>|<span data-ttu-id="1ac46-286">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-286">String</span></span>|  
|<span data-ttu-id="1ac46-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="1ac46-287">COLUMN_SIZE</span></span>|<span data-ttu-id="1ac46-288">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-288">Int32</span></span>|  
|<span data-ttu-id="1ac46-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1ac46-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="1ac46-290">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-290">Int32</span></span>|  
|<span data-ttu-id="1ac46-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="1ac46-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="1ac46-292">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-292">Int16</span></span>|  
|<span data-ttu-id="1ac46-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="1ac46-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="1ac46-294">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-294">Int16</span></span>|  
|<span data-ttu-id="1ac46-295">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="1ac46-295">NULLABLE</span></span>|<span data-ttu-id="1ac46-296">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-296">Int16</span></span>|  
|<span data-ttu-id="1ac46-297">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ac46-297">REMARKS</span></span>|<span data-ttu-id="1ac46-298">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-298">String</span></span>|  
|<span data-ttu-id="1ac46-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="1ac46-299">COLUMN_DEF</span></span>|<span data-ttu-id="1ac46-300">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-300">String</span></span>|  
|<span data-ttu-id="1ac46-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="1ac46-302">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-302">Int16</span></span>|  
|<span data-ttu-id="1ac46-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="1ac46-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="1ac46-304">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-304">Int16</span></span>|  
|<span data-ttu-id="1ac46-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1ac46-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="1ac46-306">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-306">Int32</span></span>|  
|<span data-ttu-id="1ac46-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1ac46-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="1ac46-308">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-308">Int32</span></span>|  
|<span data-ttu-id="1ac46-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="1ac46-309">IS_NULLABLE</span></span>|<span data-ttu-id="1ac46-310">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-310">String</span></span>|  
|<span data-ttu-id="1ac46-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1ac46-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="1ac46-312">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-312">String</span></span>|  
|<span data-ttu-id="1ac46-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1ac46-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="1ac46-314">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-314">String</span></span>|  
|<span data-ttu-id="1ac46-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="1ac46-316">Byte</span><span class="sxs-lookup"><span data-stu-id="1ac46-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="1ac46-317">Ovladač ODBC Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="1ac46-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="1ac46-318">Ovladač ODBC Microsoft SQL Server Oracle podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="1ac46-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="1ac46-319">Tabulky</span><span class="sxs-lookup"><span data-stu-id="1ac46-319">Tables</span></span>  
  
-   <span data-ttu-id="1ac46-320">Sloupce</span><span class="sxs-lookup"><span data-stu-id="1ac46-320">Columns</span></span>  
  
-   <span data-ttu-id="1ac46-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="1ac46-321">Procedures</span></span>  
  
-   <span data-ttu-id="1ac46-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="1ac46-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="1ac46-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="1ac46-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="1ac46-324">zobrazení</span><span class="sxs-lookup"><span data-stu-id="1ac46-324">Views</span></span>  
  
-   <span data-ttu-id="1ac46-325">Indexy</span><span class="sxs-lookup"><span data-stu-id="1ac46-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="1ac46-326">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="1ac46-326">Tables and Views</span></span>  
  
|<span data-ttu-id="1ac46-327">columnName</span><span class="sxs-lookup"><span data-stu-id="1ac46-327">ColumnName</span></span>|<span data-ttu-id="1ac46-328">Datový typ</span><span class="sxs-lookup"><span data-stu-id="1ac46-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1ac46-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="1ac46-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="1ac46-330">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-330">String</span></span>|  
|<span data-ttu-id="1ac46-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ac46-331">TABLE_OWNER</span></span>|<span data-ttu-id="1ac46-332">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-332">String</span></span>|  
|<span data-ttu-id="1ac46-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-333">TABLE_NAME</span></span>|<span data-ttu-id="1ac46-334">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-334">String</span></span>|  
|<span data-ttu-id="1ac46-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-335">TABLE_TYPE</span></span>|<span data-ttu-id="1ac46-336">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-336">String</span></span>|  
|<span data-ttu-id="1ac46-337">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ac46-337">REMARKS</span></span>|<span data-ttu-id="1ac46-338">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="1ac46-339">Sloupce</span><span class="sxs-lookup"><span data-stu-id="1ac46-339">Columns</span></span>  
  
|<span data-ttu-id="1ac46-340">columnName</span><span class="sxs-lookup"><span data-stu-id="1ac46-340">ColumnName</span></span>|<span data-ttu-id="1ac46-341">Datový typ</span><span class="sxs-lookup"><span data-stu-id="1ac46-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1ac46-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="1ac46-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="1ac46-343">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-343">String</span></span>|  
|<span data-ttu-id="1ac46-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ac46-344">TABLE_OWNER</span></span>|<span data-ttu-id="1ac46-345">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-345">String</span></span>|  
|<span data-ttu-id="1ac46-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-346">TABLE_NAME</span></span>|<span data-ttu-id="1ac46-347">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-347">String</span></span>|  
|<span data-ttu-id="1ac46-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-348">COLUMN_NAME</span></span>|<span data-ttu-id="1ac46-349">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-349">String</span></span>|  
|<span data-ttu-id="1ac46-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-350">DATA_TYPE</span></span>|<span data-ttu-id="1ac46-351">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-351">Int16</span></span>|  
|<span data-ttu-id="1ac46-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-352">TYPE_NAME</span></span>|<span data-ttu-id="1ac46-353">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-353">String</span></span>|  
|<span data-ttu-id="1ac46-354">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="1ac46-354">PRECISION</span></span>|<span data-ttu-id="1ac46-355">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-355">Int32</span></span>|  
|<span data-ttu-id="1ac46-356">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="1ac46-356">LENGTH</span></span>|<span data-ttu-id="1ac46-357">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-357">Int32</span></span>|  
|<span data-ttu-id="1ac46-358">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="1ac46-358">SCALE</span></span>|<span data-ttu-id="1ac46-359">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-359">Int16</span></span>|  
|<span data-ttu-id="1ac46-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="1ac46-360">RADIX</span></span>|<span data-ttu-id="1ac46-361">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-361">Int16</span></span>|  
|<span data-ttu-id="1ac46-362">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="1ac46-362">NULLABLE</span></span>|<span data-ttu-id="1ac46-363">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-363">Int16</span></span>|  
|<span data-ttu-id="1ac46-364">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ac46-364">REMARKS</span></span>|<span data-ttu-id="1ac46-365">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-365">String</span></span>|  
|<span data-ttu-id="1ac46-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1ac46-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="1ac46-367">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="1ac46-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="1ac46-368">Procedures</span></span>  
  
|<span data-ttu-id="1ac46-369">columnName</span><span class="sxs-lookup"><span data-stu-id="1ac46-369">ColumnName</span></span>|<span data-ttu-id="1ac46-370">Datový typ</span><span class="sxs-lookup"><span data-stu-id="1ac46-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1ac46-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="1ac46-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="1ac46-372">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-372">String</span></span>|  
|<span data-ttu-id="1ac46-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ac46-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="1ac46-374">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-374">String</span></span>|  
|<span data-ttu-id="1ac46-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="1ac46-376">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-376">String</span></span>|  
|<span data-ttu-id="1ac46-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="1ac46-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="1ac46-378">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-378">Int16</span></span>|  
|<span data-ttu-id="1ac46-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="1ac46-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="1ac46-380">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-380">Int16</span></span>|  
|<span data-ttu-id="1ac46-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="1ac46-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="1ac46-382">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-382">Int16</span></span>|  
|<span data-ttu-id="1ac46-383">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ac46-383">REMARKS</span></span>|<span data-ttu-id="1ac46-384">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-384">String</span></span>|  
|<span data-ttu-id="1ac46-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="1ac46-386">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="1ac46-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="1ac46-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="1ac46-388">columnName</span><span class="sxs-lookup"><span data-stu-id="1ac46-388">ColumnName</span></span>|<span data-ttu-id="1ac46-389">Datový typ</span><span class="sxs-lookup"><span data-stu-id="1ac46-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1ac46-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="1ac46-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="1ac46-391">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-391">String</span></span>|  
|<span data-ttu-id="1ac46-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ac46-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="1ac46-393">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-393">String</span></span>|  
|<span data-ttu-id="1ac46-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="1ac46-395">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-395">String</span></span>|  
|<span data-ttu-id="1ac46-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-396">COLUMN_NAME</span></span>|<span data-ttu-id="1ac46-397">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-397">String</span></span>|  
|<span data-ttu-id="1ac46-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-398">COLUMN_TYPE</span></span>|<span data-ttu-id="1ac46-399">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-399">Int16</span></span>|  
|<span data-ttu-id="1ac46-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-400">DATA_TYPE</span></span>|<span data-ttu-id="1ac46-401">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-401">Int16</span></span>|  
|<span data-ttu-id="1ac46-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-402">TYPE_NAME</span></span>|<span data-ttu-id="1ac46-403">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-403">String</span></span>|  
|<span data-ttu-id="1ac46-404">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="1ac46-404">PRECISION</span></span>|<span data-ttu-id="1ac46-405">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-405">Int32</span></span>|  
|<span data-ttu-id="1ac46-406">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="1ac46-406">LENGTH</span></span>|<span data-ttu-id="1ac46-407">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-407">Int32</span></span>|  
|<span data-ttu-id="1ac46-408">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="1ac46-408">SCALE</span></span>|<span data-ttu-id="1ac46-409">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-409">Int16</span></span>|  
|<span data-ttu-id="1ac46-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="1ac46-410">RADIX</span></span>|<span data-ttu-id="1ac46-411">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-411">Int16</span></span>|  
|<span data-ttu-id="1ac46-412">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="1ac46-412">NULLABLE</span></span>|<span data-ttu-id="1ac46-413">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-413">Int16</span></span>|  
|<span data-ttu-id="1ac46-414">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ac46-414">REMARKS</span></span>|<span data-ttu-id="1ac46-415">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-415">String</span></span>|  
|<span data-ttu-id="1ac46-416">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="1ac46-416">OVERLOAD</span></span>|<span data-ttu-id="1ac46-417">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-417">Int32</span></span>|  
|<span data-ttu-id="1ac46-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1ac46-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="1ac46-419">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="1ac46-420">Ovladač ODBC Microsoft Jet</span><span class="sxs-lookup"><span data-stu-id="1ac46-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="1ac46-421">Ovladač ODBC Microsoft Jet podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="1ac46-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="1ac46-422">Tabulky</span><span class="sxs-lookup"><span data-stu-id="1ac46-422">Tables</span></span>  
  
-   <span data-ttu-id="1ac46-423">Indexy</span><span class="sxs-lookup"><span data-stu-id="1ac46-423">Indexes</span></span>  
  
-   <span data-ttu-id="1ac46-424">Sloupce</span><span class="sxs-lookup"><span data-stu-id="1ac46-424">Columns</span></span>  
  
-   <span data-ttu-id="1ac46-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="1ac46-425">Procedures</span></span>  
  
-   <span data-ttu-id="1ac46-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="1ac46-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="1ac46-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="1ac46-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="1ac46-428">zobrazení</span><span class="sxs-lookup"><span data-stu-id="1ac46-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="1ac46-429">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="1ac46-429">Tables and Views</span></span>  
  
|<span data-ttu-id="1ac46-430">columnName</span><span class="sxs-lookup"><span data-stu-id="1ac46-430">ColumnName</span></span>|<span data-ttu-id="1ac46-431">Datový typ</span><span class="sxs-lookup"><span data-stu-id="1ac46-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1ac46-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="1ac46-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="1ac46-433">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-433">String</span></span>|  
|<span data-ttu-id="1ac46-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ac46-434">TABLE_OWNER</span></span>|<span data-ttu-id="1ac46-435">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-435">String</span></span>|  
|<span data-ttu-id="1ac46-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-436">TABLE_NAME</span></span>|<span data-ttu-id="1ac46-437">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-437">String</span></span>|  
|<span data-ttu-id="1ac46-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-438">TABLE_TYPE</span></span>|<span data-ttu-id="1ac46-439">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-439">String</span></span>|  
|<span data-ttu-id="1ac46-440">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ac46-440">REMARKS</span></span>|<span data-ttu-id="1ac46-441">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="1ac46-442">Sloupce</span><span class="sxs-lookup"><span data-stu-id="1ac46-442">Columns</span></span>  
  
|<span data-ttu-id="1ac46-443">columnName</span><span class="sxs-lookup"><span data-stu-id="1ac46-443">ColumnName</span></span>|<span data-ttu-id="1ac46-444">Datový typ</span><span class="sxs-lookup"><span data-stu-id="1ac46-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1ac46-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="1ac46-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="1ac46-446">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-446">String</span></span>|  
|<span data-ttu-id="1ac46-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ac46-447">TABLE_OWNER</span></span>|<span data-ttu-id="1ac46-448">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-448">String</span></span>|  
|<span data-ttu-id="1ac46-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-449">TABLE_NAME</span></span>|<span data-ttu-id="1ac46-450">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-450">String</span></span>|  
|<span data-ttu-id="1ac46-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-451">COLUMN_NAME</span></span>|<span data-ttu-id="1ac46-452">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-452">String</span></span>|  
|<span data-ttu-id="1ac46-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-453">DATA_TYPE</span></span>|<span data-ttu-id="1ac46-454">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-454">Int16</span></span>|  
|<span data-ttu-id="1ac46-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-455">TYPE_NAME</span></span>|<span data-ttu-id="1ac46-456">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-456">String</span></span>|  
|<span data-ttu-id="1ac46-457">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="1ac46-457">PRECISION</span></span>|<span data-ttu-id="1ac46-458">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-458">Int32</span></span>|  
|<span data-ttu-id="1ac46-459">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="1ac46-459">LENGTH</span></span>|<span data-ttu-id="1ac46-460">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-460">Int32</span></span>|  
|<span data-ttu-id="1ac46-461">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="1ac46-461">SCALE</span></span>|<span data-ttu-id="1ac46-462">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-462">Int16</span></span>|  
|<span data-ttu-id="1ac46-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="1ac46-463">RADIX</span></span>|<span data-ttu-id="1ac46-464">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-464">Int16</span></span>|  
|<span data-ttu-id="1ac46-465">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="1ac46-465">NULLABLE</span></span>|<span data-ttu-id="1ac46-466">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-466">Int16</span></span>|  
|<span data-ttu-id="1ac46-467">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ac46-467">REMARKS</span></span>|<span data-ttu-id="1ac46-468">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-468">String</span></span>|  
|<span data-ttu-id="1ac46-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1ac46-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="1ac46-470">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="1ac46-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="1ac46-471">Procedures</span></span>  
  
|<span data-ttu-id="1ac46-472">columnName</span><span class="sxs-lookup"><span data-stu-id="1ac46-472">ColumnName</span></span>|<span data-ttu-id="1ac46-473">Datový typ</span><span class="sxs-lookup"><span data-stu-id="1ac46-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1ac46-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="1ac46-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="1ac46-475">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-475">String</span></span>|  
|<span data-ttu-id="1ac46-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ac46-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="1ac46-477">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-477">String</span></span>|  
|<span data-ttu-id="1ac46-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="1ac46-479">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-479">String</span></span>|  
|<span data-ttu-id="1ac46-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="1ac46-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="1ac46-481">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-481">Int16</span></span>|  
|<span data-ttu-id="1ac46-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="1ac46-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="1ac46-483">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-483">Int16</span></span>|  
|<span data-ttu-id="1ac46-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="1ac46-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="1ac46-485">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-485">Int16</span></span>|  
|<span data-ttu-id="1ac46-486">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ac46-486">REMARKS</span></span>|<span data-ttu-id="1ac46-487">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-487">String</span></span>|  
|<span data-ttu-id="1ac46-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="1ac46-489">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="1ac46-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="1ac46-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="1ac46-491">columnName</span><span class="sxs-lookup"><span data-stu-id="1ac46-491">ColumnName</span></span>|<span data-ttu-id="1ac46-492">Datový typ</span><span class="sxs-lookup"><span data-stu-id="1ac46-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1ac46-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="1ac46-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="1ac46-494">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-494">String</span></span>|  
|<span data-ttu-id="1ac46-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ac46-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="1ac46-496">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-496">String</span></span>|  
|<span data-ttu-id="1ac46-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="1ac46-498">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-498">String</span></span>|  
|<span data-ttu-id="1ac46-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-499">COLUMN_NAME</span></span>|<span data-ttu-id="1ac46-500">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-500">String</span></span>|  
|<span data-ttu-id="1ac46-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-501">COLUMN_TYPE</span></span>|<span data-ttu-id="1ac46-502">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-502">Int16</span></span>|  
|<span data-ttu-id="1ac46-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-503">DATA_TYPE</span></span>|<span data-ttu-id="1ac46-504">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-504">Int16</span></span>|  
|<span data-ttu-id="1ac46-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-505">TYPE_NAME</span></span>|<span data-ttu-id="1ac46-506">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-506">String</span></span>|  
|<span data-ttu-id="1ac46-507">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="1ac46-507">PRECISION</span></span>|<span data-ttu-id="1ac46-508">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-508">Int32</span></span>|  
|<span data-ttu-id="1ac46-509">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="1ac46-509">LENGTH</span></span>|<span data-ttu-id="1ac46-510">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-510">Int32</span></span>|  
|<span data-ttu-id="1ac46-511">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="1ac46-511">SCALE</span></span>|<span data-ttu-id="1ac46-512">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-512">Int16</span></span>|  
|<span data-ttu-id="1ac46-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="1ac46-513">RADIX</span></span>|<span data-ttu-id="1ac46-514">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-514">Int16</span></span>|  
|<span data-ttu-id="1ac46-515">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="1ac46-515">NULLABLE</span></span>|<span data-ttu-id="1ac46-516">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-516">Int16</span></span>|  
|<span data-ttu-id="1ac46-517">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ac46-517">REMARKS</span></span>|<span data-ttu-id="1ac46-518">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-518">String</span></span>|  
|<span data-ttu-id="1ac46-519">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="1ac46-519">OVERLOAD</span></span>|<span data-ttu-id="1ac46-520">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-520">Int32</span></span>|  
|<span data-ttu-id="1ac46-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1ac46-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="1ac46-522">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="1ac46-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="1ac46-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="1ac46-524">columnName</span><span class="sxs-lookup"><span data-stu-id="1ac46-524">ColumnName</span></span>|<span data-ttu-id="1ac46-525">Datový typ</span><span class="sxs-lookup"><span data-stu-id="1ac46-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1ac46-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="1ac46-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="1ac46-527">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-527">String</span></span>|  
|<span data-ttu-id="1ac46-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="1ac46-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="1ac46-529">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-529">String</span></span>|  
|<span data-ttu-id="1ac46-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="1ac46-531">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-531">String</span></span>|  
|<span data-ttu-id="1ac46-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-532">COLUMN_NAME</span></span>|<span data-ttu-id="1ac46-533">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-533">String</span></span>|  
|<span data-ttu-id="1ac46-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-534">COLUMN_TYPE</span></span>|<span data-ttu-id="1ac46-535">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-535">Int16</span></span>|  
|<span data-ttu-id="1ac46-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-536">DATA_TYPE</span></span>|<span data-ttu-id="1ac46-537">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-537">Int16</span></span>|  
|<span data-ttu-id="1ac46-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="1ac46-538">TYPE_NAME</span></span>|<span data-ttu-id="1ac46-539">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-539">String</span></span>|  
|<span data-ttu-id="1ac46-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="1ac46-540">COLUMN_SIZE</span></span>|<span data-ttu-id="1ac46-541">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-541">Int32</span></span>|  
|<span data-ttu-id="1ac46-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1ac46-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="1ac46-543">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-543">Int32</span></span>|  
|<span data-ttu-id="1ac46-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="1ac46-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="1ac46-545">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-545">Int16</span></span>|  
|<span data-ttu-id="1ac46-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="1ac46-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="1ac46-547">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-547">Int16</span></span>|  
|<span data-ttu-id="1ac46-548">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="1ac46-548">NULLABLE</span></span>|<span data-ttu-id="1ac46-549">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-549">Int16</span></span>|  
|<span data-ttu-id="1ac46-550">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="1ac46-550">REMARKS</span></span>|<span data-ttu-id="1ac46-551">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-551">String</span></span>|  
|<span data-ttu-id="1ac46-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="1ac46-552">COLUMN_DEF</span></span>|<span data-ttu-id="1ac46-553">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-553">String</span></span>|  
|<span data-ttu-id="1ac46-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1ac46-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="1ac46-555">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-555">Int16</span></span>|  
|<span data-ttu-id="1ac46-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="1ac46-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="1ac46-557">Int16</span><span class="sxs-lookup"><span data-stu-id="1ac46-557">Int16</span></span>|  
|<span data-ttu-id="1ac46-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1ac46-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="1ac46-559">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-559">Int32</span></span>|  
|<span data-ttu-id="1ac46-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1ac46-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="1ac46-561">Int32</span><span class="sxs-lookup"><span data-stu-id="1ac46-561">Int32</span></span>|  
|<span data-ttu-id="1ac46-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="1ac46-562">IS_NULLABLE</span></span>|<span data-ttu-id="1ac46-563">String</span><span class="sxs-lookup"><span data-stu-id="1ac46-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ac46-564">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ac46-564">See Also</span></span>  
 [<span data-ttu-id="1ac46-565">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="1ac46-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
