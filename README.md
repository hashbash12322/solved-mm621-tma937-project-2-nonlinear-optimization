Download Link: https://assignmentchef.com/product/solved-mm621-tma937-project-2-nonlinear-optimization
<br>
Following on the previous project of building a nonlinear model that finds the optimal solution to the gas flow network in Belgium we now want to examine details of how it is possible to implement it in a mathematical programming language such as <em>AMPL</em>.

In this project we first revisit the nonlinear model that was explained in more detail in project 1 and after go to questions that analyze the behavior of the model with the help of <em>AMPL</em>.




<h1><a name="_Toc25308"></a>1           Model description</h1>

The sets of the model <em>I </em>= {All towns represented by Table <strong>??</strong>}

<em>P </em>= {All passive edges }

<em>A </em>= {All active edges}

<em>E </em>= {All edges} = {P ∪ <em>A</em>}

And the <strong>parameters </strong>of our model

<em>L<sub>ij </sub></em>= ”Length in km of the pipe between town i and town <em>j</em>.”

<em>D<sub>ij </sub></em>= ”Interior diameter of the pipe in mm between town <em>i </em>and town <em>j</em>.”

= ”Minimum quantity of 10<sup>6</sup><em>m</em><sup>3 </sup>gas / day to town <em>j</em>.”

= ”Maximum quantity of 10<sup>6</sup><em>m</em><sup>3 </sup>gas / day to town <em>j</em>. ”

= ”Minimum pressure in bar in town <em>j</em>.”

= ”Maximum pressure in bar in town <em>j</em>.” <em>c<sub>j </sub></em>= ”Cost in [$<em>/m</em><sup>3</sup>] to buy to town <em>j</em>”

<em>K </em>= ”Constant to convert BTU to <em>m</em><sup>3</sup>”

<em>z </em>= ”Gas compressibility factor”

Lastly the <strong>variables </strong>for our model will be

<em>f<sub>ij </sub></em>= ”Flow of gas from town i to town j” <em>x<sub>j </sub></em>= ”Net result of gas in 10<sup>6</sup><em>m</em><sup>3 </sup>/ day to town j” <em>p<sub>j </sub></em>= ”Pressure of gas in bar in town j”

And the following numerical constants:

(1)

With everything declared the model is

minimize X<em>Kc</em><em>jx</em><em>j x</em>∈<em>I j</em>∈<em>I</em>

s.t.

<em>x<sub>j                                      </sub></em>= X<em>f</em><em>ji </em>− X<em>f</em><em>ij, </em>∀<em>j </em>∈ <em>I</em>

<em>i</em>∈<em>I                      i</em>∈<em>I</em>

<em>x<sub>j </sub></em> <em>I x<sub>j </sub></em>≥ <em>q</em><em>jmin, </em>∀<em>j </em>∈ <em>I p<sub>j </sub></em>≤ <em>I</em>

<table width="232">

 <tbody>

  <tr>

   <td width="62"><em>p<sub>j</sub></em></td>

   <td width="24">≥</td>

   <td width="146">             <em>p</em><em>minj    , </em>∀<em>j </em>∈ <em>I</em></td>

  </tr>

  <tr>

   <td width="62">|<em>f</em><em>ij</em>|<em>f</em><em>ij</em></td>

   <td width="24">=</td>

   <td width="146"><em>C<sub>ij</sub></em><sup>2 </sup>(<em>p</em><sup>2</sup><em><sub>i </sub></em>− <em>p</em><sup>2</sup><em><sub>j</sub></em>)<em>, </em>∀ (<em>i,j</em>) ∈ <em>P</em></td>

  </tr>

  <tr>

   <td width="62">|<em>f</em><em>ij</em>|<em>f</em><em>ij</em></td>

   <td width="24">≥</td>

   <td width="146"><em>C<sub>ij</sub></em><sup>2 </sup>(<em>p</em><sup>2</sup><em><sub>i </sub></em>− <em>p</em><sup>2</sup><em><sub>j</sub></em>)<em>, </em>∀ (<em>i,j</em>) ∈ <em>A</em></td>

  </tr>

  <tr>

   <td width="62"><em>f</em><em>ij</em></td>

   <td width="24">≥</td>

   <td width="146">0<em>, </em>(<em>i,j</em>) ∈ <em>A</em></td>

  </tr>

  <tr>

   <td width="62"><em>f</em><em>ij</em></td>

   <td width="24">=</td>

   <td width="146">0<em>, </em>(<em>i,j</em>) 6∈ <em>E</em></td>

  </tr>

 </tbody>

</table>

From <em>AMPL</em>, using the optimizer Baron, we run this model and obtain the following table for the flow.

<table width="611">

 <tbody>

  <tr>

   <td width="56"> </td>

   <td width="56">Antwerpen</td>

   <td width="47">Arlon</td>

   <td width="40">Brugge</td>

   <td width="45">Gent</td>

   <td width="37">Liege</td>

   <td width="45">Mons</td>

   <td width="45">Namur</td>

   <td width="47">Sinsin</td>

   <td width="40">Voeren</td>

   <td width="47">Warnant</td>

   <td width="53">Zeebrugge</td>

   <td width="54">Zomergem</td>

  </tr>

  <tr>

   <td width="56">Antwerpen</td>

   <td width="56">0</td>

   <td width="47">0</td>

   <td width="40">0</td>

   <td width="45">-4.10082</td>

   <td width="37">0</td>

   <td width="45">0</td>

   <td width="45">0</td>

   <td width="47">0</td>

   <td width="40">0</td>

   <td width="47">0</td>

   <td width="53">0</td>

   <td width="54">0</td>

  </tr>

  <tr>

   <td width="56">Arlon</td>

   <td width="56">0</td>

   <td width="47">0</td>

   <td width="40">0</td>

   <td width="45">0</td>

   <td width="37">0</td>

   <td width="45">0</td>

   <td width="45">0</td>

   <td width="47">0</td>

   <td width="40">0</td>

   <td width="47">0</td>

   <td width="53">0</td>

   <td width="54">0</td>

  </tr>

  <tr>

   <td width="56">Brugge</td>

   <td width="56">0</td>

   <td width="47">0</td>

   <td width="40">0</td>

   <td width="45">0</td>

   <td width="37">0</td>

   <td width="45">0</td>

   <td width="45">0</td>

   <td width="47">0</td>

   <td width="40">0</td>

   <td width="47">0</td>

   <td width="53">0</td>

   <td width="54">4.8791</td>

  </tr>

  <tr>

   <td width="56">Gent</td>

   <td width="56">0</td>

   <td width="47">0</td>

   <td width="40">0</td>

   <td width="45">0</td>

   <td width="37">0</td>

   <td width="45">0</td>

   <td width="45">0</td>

   <td width="47">0</td>

   <td width="40">0</td>

   <td width="47">0</td>

   <td width="53">0</td>

   <td width="54">-9.43006</td>

  </tr>

  <tr>

   <td width="56">Liege</td>

   <td width="56">0</td>

   <td width="47">0</td>

   <td width="40">0</td>

   <td width="45">0</td>

   <td width="37">0</td>

   <td width="45">0</td>

   <td width="45">0</td>

   <td width="47">0</td>

   <td width="40">0</td>

   <td width="47">13.9139</td>

   <td width="53">0</td>

   <td width="54">0</td>

  </tr>

  <tr>

   <td width="56">Mons</td>

   <td width="56">0</td>

   <td width="47">0</td>

   <td width="40">0</td>

   <td width="45">0</td>

   <td width="37">0</td>

   <td width="45">0</td>

   <td width="45">-11.4722</td>

   <td width="47">0</td>

   <td width="40">0</td>

   <td width="47">0</td>

   <td width="53">0</td>

   <td width="54">0</td>

  </tr>

  <tr>

   <td width="56">Namur</td>

   <td width="56">0</td>

   <td width="47">0</td>

   <td width="40">0</td>

   <td width="45">0</td>

   <td width="37">0</td>

   <td width="45">0</td>

   <td width="45">0</td>

   <td width="47">0</td>

   <td width="40">0</td>

   <td width="47">-13.6629</td>

   <td width="53">0</td>

   <td width="54">0</td>

  </tr>

  <tr>

   <td width="56">Sinsin</td>

   <td width="56">0</td>

   <td width="47">0.251012</td>

   <td width="40">0</td>

   <td width="45">0</td>

   <td width="37">0</td>

   <td width="45">0</td>

   <td width="45">0</td>

   <td width="47">0</td>

   <td width="40">0</td>

   <td width="47">0</td>

   <td width="53">0</td>

   <td width="54">0</td>

  </tr>

  <tr>

   <td width="56">Voeren</td>

   <td width="56">0</td>

   <td width="47">0</td>

   <td width="40">0</td>

   <td width="45">0</td>

   <td width="37">20.344</td>

   <td width="45">0</td>

   <td width="45">0</td>

   <td width="47">0</td>

   <td width="40">0</td>

   <td width="47">0</td>

   <td width="53">0</td>

   <td width="54">0</td>

  </tr>

  <tr>

   <td width="56">Warnant</td>

   <td width="56">0</td>

   <td width="47">0</td>

   <td width="40">0</td>

   <td width="45">0</td>

   <td width="37">0</td>

   <td width="45">0</td>

   <td width="45">0</td>

   <td width="47">0.251012</td>

   <td width="40">0</td>

   <td width="47">0</td>

   <td width="53">0</td>

   <td width="54">0</td>

  </tr>

  <tr>

   <td width="56">Zeebrugge</td>

   <td width="56">0</td>

   <td width="47">0</td>

   <td width="40">8.87</td>

   <td width="45">0</td>

   <td width="37">0</td>

   <td width="45">0</td>

   <td width="45">0</td>

   <td width="47">0</td>

   <td width="40">0</td>

   <td width="47">0</td>

   <td width="53">0</td>

   <td width="54">0</td>

  </tr>

  <tr>

   <td width="56">Zomergem</td>

   <td width="56">0</td>

   <td width="47">0</td>

   <td width="40">0</td>

   <td width="45">0</td>

   <td width="37">0</td>

   <td width="45">-4.55097</td>

   <td width="45">0</td>

   <td width="47">0</td>

   <td width="40">0</td>

   <td width="47">0</td>

   <td width="53">0</td>

   <td width="54">0</td>

  </tr>

 </tbody>

</table>

Table 1: Table of flows.

<h1><a name="_Toc25309"></a>2           Questions, group I</h1>

Using the solver Baron!

<ol>

 <li><em>What is the total cost of the gas supplying the demands in Belgium?</em>The total cost is given by</li>

</ol>

minimize <sup>X</sup><em>Kc<sub>j</sub>x<sub>j                  </sub></em>(2) <em>x</em>∈<em>I j</em>∈<em>I</em>

which when running the solver with <em>AMPL </em>returns the value <em>f</em><sup>∗ </sup>= 1921171<em>.</em>317 which is in given in $.

<ol start="2">

 <li><em>How much gas should be sent from Zomergem to Gent?</em></li>

</ol>

From <em>AMPL </em>we obtain the Table 1 where we note that from Gent to Zomergem there is a flow of -9.43006 which means that from Zomergem to Gent it is 9.43006 <em>million m</em><sup>3</sup><em>/day</em>.

<ol start="3">

 <li><em>How much Algerian gas should be purchased?</em></li>

</ol>

Similarly as in the previous question we can note that from the table we send a total of 8.87 million <em>m</em><sup>3 </sup>gas from Zeebrugge which means that from Algeria we need to buy that same amount.

<ol start="4">

 <li><em>How much gas is being transported from Warnant to Sinsin as a result of the compressor working on thisactive pipeline?</em></li>

</ol>

We note that for the active edge we have the following relation between flow

|<em>f<sub>ij</sub></em>|<em>f<sub>ij </sub></em>≥ <em>C<sub>ij</sub></em><sup>2 </sup>(<em>p</em><sup>2</sup><em><sub>i </sub></em>− <em>p</em><sup>2</sup><em><sub>j</sub></em>)<em>, </em>∀ (<em>i,j</em>) ∈ <em>P                                                                          </em>(3)

This relationship is equality for a passive edge. We can compare the difference between the left handside and the right handside, which in this case would be

|<em>f<sub>ij</sub></em>|<em>f<sub>ij </sub></em>− <em>C<sub>ij</sub></em><sup>2 </sup>(<em>p</em><sup>2</sup><em><sub>i </sub></em>− <em>p</em><sup>2</sup><em><sub>j</sub></em>) = 0<em>.</em>251012<sup>2 </sup>− 0<em>.</em>00413627 ∗ (2160<em>.</em>46 − 2402<em>.</em>74) = 1<em>.</em>06514252

And this would describe how much gas is being transported as a result of the compressor working on this active pipeline. In this case doing this calculation results in approximately 1<em>.</em>065 million <em>m</em><sup>3 </sup>gas being transported.

<h1><a name="_Toc25310"></a>3           Questions, group II</h1>

<ol>

 <li><em>Is the solution obtained locally optimal? Globally optimal? Explain your answers. Also explain if the approach you adopt to verify optimality works in general cases beyond this exercise.</em></li>

</ol>

The solution obtained is globally optimal. This is because we buy the lowest amount that is possible from constrains (purchasing 344 from Voeren and <em>x<sub>Zeebrugge </sub></em>= <em>q<sub>Zeebrugge</sub><sup>min </sup></em>= 8<em>.</em>870. Since the objective function is to minimize the cost of purchase, no other purchase from Norway( <em>x<sub>V oeren</sub></em>) and Algeria

(<em>x<sub>Zeebrugge</sub></em>) can be better.

This approach of course can not be used in general cases, since an optimum can lie in other points than in the boundary of the constraints.

<ol start="2">

 <li><em>In the given AMPL model, the pressure-related decision variables are not exactly the pressures at the nodes.What are these decision variables? Why can we use these variables, and why do we want to use them?</em></li>

</ol>

The decision variables are not the pressure at the nodes, but rather the pressures at the nodes squared. If we look at the constraints

|<em>f</em><em>ij</em>|<em>f</em><em>ij </em>= <em>C</em><em>ij</em>2 (<em>p</em>2<em>i </em>− <em>p</em>2<em>j</em>)

We notice that we can make the <em>p<sub>i</sub></em>’s linear by squaring them. This makes the constraints easier to solve, since the problem then becomes

|<em>f</em><em>ij</em>|<em>f</em><em>ij </em>= <em>C</em><em>ij</em>2 (<em>p</em>˜<em>i </em>− <em>p</em>˜<em>j</em>)

which is more linear than previously. In general linear programs are much easier to solve than nonlinear, hence if it possible to make it more linear by squaring the constants we wish to do so.

<ol start="3">

 <li><em>Describe conceptually how to find a feasible solution without using any given nonlinear programming solver(this is useful in case the solver actually requires you to provide a feasible initial solution).</em></li>

</ol>

One method of finding a feasible initial solution can be described as follows.

Fix the flows in all edges, so that the flow in each edge follows the constrains of <em>q<sub>j</sub><sup>min</sup></em>. For example, set and

and <em>x<sub>Zeebrugge </sub></em>= <em>q<sub>max</sub><sup>Zeebrugge</sup></em>. Let us focus on the flow from Voeren. Let the flow from Voeren

to Li`ege equal to the miniumum amount of demand at that node, in this case <em>f<sub>V oeren,Liege</sub></em><sub>` </sub>= −6<em>.</em>365. Now, in the equation

|<em>f</em><em>ij</em>|<em>f</em><em>ij </em>= <em>C</em><em>ij</em>2 (<em>p</em>2<em>i </em>− <em>p</em>2<em>j</em>)                                                                                   (4)

(the index i here being the city Voeren), let the initial pressure <em>p<sub>i </sub></em>= <em>p<sub>initial </sub></em>= <em>p<sup>max</sup><sub>i </sub></em>. By doing this, we now only have one unknown <em>p<sub>j</sub></em>, which is solvable. Solve for <em>p<sub>j</sub></em>. Move from Li´ege to Warnant, and use the same equation as before. The new <em>p<sub>i </sub></em>in Eq. (4) is the previous <em>p<sub>j </sub></em>that we just solved. Now, since the <em>f<sub>ij</sub></em>’s and the <em>p<sub>i</sub></em>’s are known, we again solve for <em>p<sub>j</sub></em>. If we can make the left hand side equal to the right hand side, then we continue until we have set all the pressures at the nodes (we have a feasible solution). If we can not make the constraint hold by setting a new <em>p<sub>j </sub></em>(the right hand can’t be equal to the left hand side by any feasible <em>p<sub>j</sub></em>), then we need to reduce the initial pressure by multiplying the initial pressure as <em>p<sub>initial </sub></em>← 0<em>.</em>99 <em>p<sub>initial</sub></em>. And then we repeat this until we obtain a feasible solution.

Of course, we would similarly do this when we consider the flow from Algeria in town Zeebrugge.

<h1><a name="_Toc25311"></a>4           Questions, group III</h1>

<ol>

 <li><em> Assume that Norwegian gas supply is reduced. Specifically, both the minimum and maximum quantities of the supply from Voeren are reduced to 80% of their original values.</em></li>

 <li><em>How does the total amount of Algerian gas purchased change?</em></li>

</ol>

When reoptimizing using 80% of the minimum and maximum quantity we obtain a new optimum that instead of buying 8<em>.</em>87 million <em>m</em><sup>3 </sup>we instead buy 11.1534. Therefore the change is 11<em>.</em>1534 − 8<em>.</em>87 = 2<em>.</em>2834.

<ol>

 <li><em>How does the total amount of Norwegian gas purchased change?</em></li>

</ol>

We go from having an previous optimum at 20.344 to 17.6096, hence the change is 20<em>.</em>344 − 17<em>.</em>6096 = 2<em>.</em>7344. <em>c) Explain why the above changes occur!</em>

Previously we bought the minimum requirement from both Norway and Algeria, whereas when changing the lower bound on required purchase from Norway the new amount we buy from Norway is now instead the upperbound of what we can buy. This is most likely because in order to satisfy all towns demand we need to buy more than what is the updated minimum amount from both Norway and Algeria. When this is the case we then notice that we buy the maximum possible from Norway and the reason is quite simple since buying from Norway is cheaper then Algeria.

<ol start="2">

 <li><em>What and how much can be changed in the data of the problem to make the compressor on the pipeline fromWarnant to Sinsin active? How can you tell the compressor is indeed active? Hint: the answer to thisquestion need not be unique.</em></li>

</ol>

One idea is changing the demand of the town Arlon and increasing this demand would at some point require that the compressor is active. In this case if we change the required demand of Arlon from −0<em>.</em>222 to −1<em>.</em>8 the compressor becomes activate which is seen easily as the pressure from Warnant to Sinsin is increased. If we keep increasing the demand further we will come to a point where the problem becomes infeasible.

<ol start="3">

 <li><em>Consider the case of increased demands:</em></li>

 <li><em>The demands at all demand nodes are doubled, while the supply ateach supply node remains the same. Is thisoptimization model feasible? Explain your answer.</em></li>

</ol>

Before doubling the demands, the total gas demand for all nodes equals −3<em>.</em>918−4<em>.</em>034−5<em>.</em>256−6<em>.</em>365−2<em>.</em>120− 6<em>.</em>848 + 0<em>.</em>222 = 28<em>.</em>763 which is less than the total capacity of 22<em>.</em>012 + 11<em>.</em>594 = 33<em>.</em>606. But when we double the demands we get that the demand is equal to 28<em>.</em>763∗2 = 57<em>.</em>526, which is greater than total capcity 33.606.

Hence, we can clearly say that it is infeasible.

<ol>

 <li><em>The demands at all demand nodes are doubled, and the maximum supplies at all supply nodes are also doubled.Is this optimization model feasible? Explain your answer. Hint: make sure you use the appropriate solver to make your statement.</em></li>

</ol>

In this case it is not clear to say that it is infeasible. This is because, as previously, we see that the sum of the demands (doubled) is 57<em>.</em>526, but doubling the supply/capacity gives 2 ∗ 33<em>.</em>606 = 67<em>.</em>212, so the sum of the demands are less than the total capacity. But this does not necessarily mean that we have a feasible solution either, as we have additional constraints that should be met. If we use these new demands and supplies and try to optimize with <em>AMPL </em>we obtain that with both snopt, baron and trying other solvers that the problem is infeasible. With the optimizer snopt there is a statement that ’infeasibilities minimized’, but the problem is still infeasible. We know that if we double the supply and demand the infeasibilities must be connected to the pressure requirements. Particularly we notice that a consequence of this, which is easily checked, is that the intermediate nodes results in not having a zero net flow. Take for example the column of Zomergem in Table

<ol start="2">

 <li>2. The sum of this column is not zero, meaning that the flow is not zero for this intermediate node, leading to a violation of the constraints.</li>

</ol>

<table width="693">

 <tbody>

  <tr>

   <td width="90"> </td>

   <td width="90"><strong>Antwerpen</strong></td>

   <td width="85"><strong>Arlon</strong></td>

   <td width="87"><strong>Brugge</strong></td>

   <td width="51"><strong>Gent</strong></td>

   <td width="53"><strong>Liege</strong></td>

   <td width="53"><strong>Mons</strong></td>

   <td width="63"><strong>Namur</strong></td>

   <td width="56"><strong>Sinsin</strong></td>

   <td width="64"><strong>Voeren</strong></td>

  </tr>

  <tr>

   <td width="90"><strong>Antwerpen</strong></td>

   <td width="90">0</td>

   <td width="85">0</td>

   <td width="87">0</td>

   <td width="51">-8.068</td>

   <td width="53">0</td>

   <td width="53">0</td>

   <td width="63">0</td>

   <td width="56">0</td>

   <td width="64">0</td>

  </tr>

  <tr>

   <td width="90"><strong>Arlon</strong></td>

   <td width="90">0</td>

   <td width="85">0</td>

   <td width="87">0</td>

   <td width="51">0</td>

   <td width="53">0</td>

   <td width="53">0</td>

   <td width="63">0</td>

   <td width="56">0</td>

   <td width="64">0</td>

  </tr>

  <tr>

   <td width="90"><strong>Brugge</strong></td>

   <td width="90">0</td>

   <td width="85">0</td>

   <td width="87">0</td>

   <td width="51">0</td>

   <td width="53">0</td>

   <td width="53">0</td>

   <td width="63">0</td>

   <td width="56">0</td>

   <td width="64">0</td>

  </tr>

  <tr>

   <td width="90"><strong>Gent</strong></td>

   <td width="90">0</td>

   <td width="85">0</td>

   <td width="87">0</td>

   <td width="51">0</td>

   <td width="53">0</td>

   <td width="53">0</td>

   <td width="63">0</td>

   <td width="56">0</td>

   <td width="64">0</td>

  </tr>

  <tr>

   <td width="90"><strong>Liege</strong></td>

   <td width="90">0</td>

   <td width="85">0</td>

   <td width="87">0</td>

   <td width="51">0</td>

   <td width="53">0</td>

   <td width="53">0</td>

   <td width="63">0</td>

   <td width="56">0</td>

   <td width="64">0</td>

  </tr>

  <tr>

   <td width="90"><strong>Mons</strong></td>

   <td width="90">0</td>

   <td width="85">0</td>

   <td width="87">0</td>

   <td width="51">0</td>

   <td width="53">0</td>

   <td width="53">0</td>

   <td width="63">-16.924</td>

   <td width="56">0</td>

   <td width="64">0</td>

  </tr>

  <tr>

   <td width="90"><strong>Namur</strong></td>

   <td width="90">0</td>

   <td width="85">0</td>

   <td width="87">0</td>

   <td width="51">0</td>

   <td width="53">0</td>

   <td width="53">0</td>

   <td width="63">0</td>

   <td width="56">0</td>

   <td width="64">0</td>

  </tr>

  <tr>

   <td width="90"><strong>Sinsin</strong></td>

   <td width="90">0</td>

   <td width="85">0.444</td>

   <td width="87">0</td>

   <td width="51">0</td>

   <td width="53">0</td>

   <td width="53">0</td>

   <td width="63">0</td>

   <td width="56">0</td>

   <td width="64">0</td>

  </tr>

  <tr>

   <td width="90"><strong>Voeren</strong></td>

   <td width="90">0</td>

   <td width="85">0</td>

   <td width="87">0</td>

   <td width="51">0</td>

   <td width="53">40.688</td>

   <td width="53">0</td>

   <td width="63">0</td>

   <td width="56">0</td>

   <td width="64">0</td>

  </tr>

  <tr>

   <td width="90"><strong>Warnant</strong></td>

   <td width="90">0</td>

   <td width="85">0</td>

   <td width="87">0</td>

   <td width="51">0</td>

   <td width="53">0</td>

   <td width="53">0</td>

   <td width="63">0</td>

   <td width="56">0.444</td>

   <td width="64">0</td>

  </tr>

  <tr>

   <td width="90"><strong>Zeebrugge</strong></td>

   <td width="90">0</td>

   <td width="85">0</td>

   <td width="87">23.188</td>

   <td width="51">0</td>

   <td width="53">0</td>

   <td width="53">0</td>

   <td width="63">0</td>

   <td width="56">0</td>

   <td width="64">0</td>

  </tr>

  <tr>

   <td width="90"><strong>Zomergem</strong></td>

   <td width="90">0</td>

   <td width="85">0</td>

   <td width="87">0</td>

   <td width="51">0</td>

   <td width="53">0</td>

   <td width="53">-3.228</td>

   <td width="63">0</td>

   <td width="56">0</td>

   <td width="64">0</td>

  </tr>

  <tr>

   <td width="90"> </td>

   <td width="90"><strong>Warnant</strong></td>

   <td width="85"><strong>Zeebrugge</strong></td>

   <td width="87"><strong>Zomergem</strong></td>

   <td rowspan="13" width="51"> </td>

   <td rowspan="13" width="53"> </td>

   <td rowspan="13" width="53"> </td>

   <td rowspan="13" width="63"> </td>

   <td rowspan="13" width="56"> </td>

   <td rowspan="13" width="64"> </td>

  </tr>

  <tr>

   <td width="90"><strong>Antwerpen</strong></td>

   <td width="90">0</td>

   <td width="85">0</td>

   <td width="87">0</td>

  </tr>

  <tr>

   <td width="90"><strong>Arlon</strong></td>

   <td width="90">0</td>

   <td width="85">0</td>

   <td width="87">0</td>

  </tr>

  <tr>

   <td width="90"><strong>Brugge</strong></td>

   <td width="90">0</td>

   <td width="85">0</td>

   <td width="87">15.352</td>

  </tr>

  <tr>

   <td width="90"><strong>Gent</strong></td>

   <td width="90">0</td>

   <td width="85">0</td>

   <td width="87">-18.58</td>

  </tr>

  <tr>

   <td width="90"><strong>Liege</strong></td>

   <td width="90">21.608</td>

   <td width="85">0</td>

   <td width="87">0</td>

  </tr>

  <tr>

   <td width="90"><strong>Mons</strong></td>

   <td width="90">0</td>

   <td width="85">0</td>

   <td width="87">0</td>

  </tr>

  <tr>

   <td width="90"><strong>Namur</strong></td>

   <td width="90">-21.164</td>

   <td width="85">0</td>

   <td width="87">0</td>

  </tr>

  <tr>

   <td width="90"><strong>Sinsin</strong></td>

   <td width="90">0</td>

   <td width="85">0</td>

   <td width="87">0</td>

  </tr>

  <tr>

   <td width="90"><strong>Voeren</strong></td>

   <td width="90">0</td>

   <td width="85">0</td>

   <td width="87">0</td>

  </tr>

  <tr>

   <td width="90"><strong>Warnant</strong></td>

   <td width="90">0</td>

   <td width="85">0</td>

   <td width="87">0</td>

  </tr>

  <tr>

   <td width="90"><strong>Zeebrugge</strong></td>

   <td width="90">0</td>

   <td width="85">0</td>

   <td width="87">0</td>

  </tr>

  <tr>

   <td width="90"><strong>Zomergem</strong></td>

   <td width="90">0</td>

   <td width="85">0</td>

   <td width="87">0</td>

  </tr>

 </tbody>

</table>

Table 2: Table showing the flows of the optimization problem using the optimizer snopt.exe after dubbling the supplies and demands.

<ol start="4">

 <li><em> Consider the marginal reductions of the minimal supplies of Norwegianand Algerian gas. Consider one limit at a time. What are the approxi-mate derivatives of the total cost with respect to changes of the minimalsupplies of Norwegian and Algerian gas, evaluated at the original opti-mal solution? Describe how you obtain these approximate derivatives.In addition, compare the results with the values of the dual variables forthe limiting constraints in the optimal solution to the original problem.</em></li>

</ol>

We utilize directional derivative given by

(5)

And similarly defined for ). The idea here is that we can choose ∆ equal to a small value, say for example ∆ = 0<em>.</em>001, or perhaps even smaller and instead approximate the derivative with numerical answers provided by <em>AMPL</em>. Notice that in this case the function we are trying to minimize depends on two variables, i.e the amount of gas we buy from Norway to Voeren (V) and Algeria to Zeebrugge (Z). Doing these reoptimizations and simple calculations with ∆ = 0<em>.</em>00001 we obtain

and

Interestingly one can also compare with the dual variables solution for the limiting constraints and one obtains the numerical values 59328<em>.</em>6 and 80517<em>.</em>4. Illustrating the relationship between the derivative and solution of the dual problem, even though the problem is not entirely linear.