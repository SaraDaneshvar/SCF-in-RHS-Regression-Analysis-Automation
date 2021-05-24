# SCF-in-RHS-Regression-Analysis-Automation
# -*- coding: mbcs -*-
from part import *
from material import *
from section import *
from assembly import *
from step import *
from interaction import *
from load import *
from mesh import *
from optimization import *
from job import *
from sketch import *
from visualization import *
from connectorBehavior import *


def fea(b0, t0, b1, t1):
    """Finite Element Analysis (FEA) Automation

    Create the parts, assemble them, mesh the assembly, and run the analysis.
    The stresses are then exported to Excel, where we extrapolate the stress at other points using regression analysis.
    """

    mdb.models['Model-1'].ConstrainedSketch(name='__profile__', sheetSize=200.0)
    mdb.models['Model-1'].sketches['__profile__'].rectangle(point1=(0.0, 0.0),
        point2=(88.9, 88.9))
    mdb.models['Model-1'].sketches['__profile__'].offset(distance=9.74, objectList=
        (mdb.models['Model-1'].sketches['__profile__'].geometry[2],
        mdb.models['Model-1'].sketches['__profile__'].geometry[3],
        mdb.models['Model-1'].sketches['__profile__'].geometry[4],
        mdb.models['Model-1'].sketches['__profile__'].geometry[5]), side=LEFT)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[9], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[8], nearPoint1=(
        9.15232467651367, 46.7179641723633), nearPoint2=(28.120174407959,
        77.7084350585938), radius=7.94)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[8], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[7], nearPoint1=(
        63.2458610534668, 78.0605926513672), nearPoint2=(77.2961120605469,
        72.7781372070313), radius=7.94)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[7], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[6], nearPoint1=(
        77.9986419677734, 62.2131958007813), nearPoint2=(51.6543846130371,
        10.4450359344482), radius=7.94)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[6], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[9], nearPoint1=(
        47.4392967224121, 9.38854789733887), nearPoint2=(10.2060813903809,
        26.2924251556396), radius=7.94)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[3], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[2], nearPoint1=(
        57.6257286071777, 87.5690307617188), nearPoint2=(0.722148895263672,
        68.9043121337891), radius=15.88)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[2], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[5], nearPoint1=(
        -0.682880401611328, 59.0437240600586), nearPoint2=(13.0161399841309,
        2.34525871276855), radius=15.88)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[5], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[4], nearPoint1=(
        30.2277030944824, 1.64092826843262), nearPoint2=(89.2388305664063,
        26.2924251556396), radius=15.88)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[4], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[3], nearPoint1=(
        89.2388305664063, 30.1662425994873), nearPoint2=(71.676025390625,
        90.3863525390625), radius=15.88)
    mdb.models['Model-1'].Part(dimensionality=THREE_D, name='Brace', type=
        DEFORMABLE_BODY)
    mdb.models['Model-1'].parts['Brace'].BaseSolidExtrude(depth=260.0, sketch=
        mdb.models['Model-1'].sketches['__profile__'])
    del mdb.models['Model-1'].sketches['__profile__']
    mdb.models['Model-1'].ConstrainedSketch(name='__profile__', sheetSize=200.0)
    mdb.models['Model-1'].sketches['__profile__'].rectangle(point1=(0.0, 0.0),
        point2=(177.8, 177.8))
    mdb.models['Model-1'].sketches['__profile__'].offset(distance=12.7, objectList=
        (mdb.models['Model-1'].sketches['__profile__'].geometry[2],
        mdb.models['Model-1'].sketches['__profile__'].geometry[3],
        mdb.models['Model-1'].sketches['__profile__'].geometry[4],
        mdb.models['Model-1'].sketches['__profile__'].geometry[5]), side=LEFT)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[9], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[8], nearPoint1=(
        9.5936279296875, 110.462860107422), nearPoint2=(73.9898223876953,
        161.667663574219), radius=12.7)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[8], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[7], nearPoint1=(
        91.0141143798828, 161.667663574219), nearPoint2=(167.253265380859,
        132.725830078125), radius=12.7)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[7], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[6], nearPoint1=(
        165.03271484375, 131.241607666016), nearPoint2=(107.298187255859,
        16.958423614502), radius=12.7)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[6], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[9], nearPoint1=(
        110.999145507813, 13.2479286193848), nearPoint2=(11.814208984375,
        57.773868560791), radius=12.7)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[5], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[4], nearPoint1=(
        83.6122436523438, 5.0848274230957), nearPoint2=(180.576599121094,
        36.2529792785645), radius=25.4)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[4], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[3], nearPoint1=(
        179.836456298828, 52.5791664123535), nearPoint2=(147.268249511719,
        177.251739501953), radius=25.4)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[3], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[2], nearPoint1=(
        128.023406982422, 179.478057861328), nearPoint2=(-3.72970581054688,
        143.857299804688), radius=25.4)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[2], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[5], nearPoint1=(
        -2.989501953125, 142.373107910156), nearPoint2=(83.6122436523438,
        3.60063552856445), radius=25.4)
    mdb.models['Model-1'].Part(dimensionality=THREE_D, name='Chord', type=
        DEFORMABLE_BODY)
    mdb.models['Model-1'].parts['Chord'].BaseSolidExtrude(depth=1050.0, sketch=
        mdb.models['Model-1'].sketches['__profile__'])
    del mdb.models['Model-1'].sketches['__profile__']
    mdb.models['Model-1'].Material(name='Steel')
    mdb.models['Model-1'].materials['Steel'].Elastic(table=((205.0, 0.3), ))
    mdb.models['Model-1'].HomogeneousSolidSection(material='Steel', name='Steel',
        thickness=None)
    mdb.models['Model-1'].parts['Chord'].Set(cells=
        mdb.models['Model-1'].parts['Chord'].cells.getSequenceFromMask(('[#1 ]', ),
        ), name='Set-1')
    mdb.models['Model-1'].parts['Chord'].SectionAssignment(offset=0.0, offsetField=
        '', offsetType=MIDDLE_SURFACE, region=
        mdb.models['Model-1'].parts['Chord'].sets['Set-1'], sectionName='Steel',
        thicknessAssignment=FROM_SECTION)
    mdb.models['Model-1'].parts['Brace'].Set(cells=
        mdb.models['Model-1'].parts['Brace'].cells.getSequenceFromMask(('[#1 ]', ),
        ), name='Set-1')
    mdb.models['Model-1'].parts['Brace'].SectionAssignment(offset=0.0, offsetField=
        '', offsetType=MIDDLE_SURFACE, region=
        mdb.models['Model-1'].parts['Brace'].sets['Set-1'], sectionName='Steel',
        thicknessAssignment=FROM_SECTION)
    mdb.models['Model-1'].ConstrainedSketch(name='__profile__', sheetSize=200.0)
    mdb.models['Model-1'].sketches['__profile__'].Line(point1=(0.0, 0.0), point2=(
        0.0, 12.0))
    mdb.models['Model-1'].sketches['__profile__'].VerticalConstraint(addUndoState=
        False, entity=mdb.models['Model-1'].sketches['__profile__'].geometry[2])
    mdb.models['Model-1'].sketches['__profile__'].Line(point1=(0.0, 12.0), point2=(
        4.0, 0.0))
    mdb.models['Model-1'].sketches['__profile__'].Line(point1=(4.0, 0.0), point2=(
        0.0, 0.0))
    mdb.models['Model-1'].sketches['__profile__'].HorizontalConstraint(
        addUndoState=False, entity=
        mdb.models['Model-1'].sketches['__profile__'].geometry[4])
    mdb.models['Model-1'].Part(dimensionality=THREE_D, name='SideWeld', type=
        DEFORMABLE_BODY)
    mdb.models['Model-1'].parts['SideWeld'].BaseSolidExtrude(depth=57.14, sketch=
        mdb.models['Model-1'].sketches['__profile__'])
    del mdb.models['Model-1'].sketches['__profile__']
    mdb.models['Model-1'].rootAssembly.DatumCsysByDefault(CARTESIAN)
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='Brace-1', part=
        mdb.models['Model-1'].parts['Brace'])
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='Chord-1', part=
        mdb.models['Model-1'].parts['Chord'])
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='SideWeld-1',
        part=mdb.models['Model-1'].parts['SideWeld'])
    mdb.models['Model-1'].rootAssembly.instances['Chord-1'].translate(vector=(
        106.68, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.instances['SideWeld-1'].translate(vector=(
        284.88, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.rotate(angle=90.0, axisDirection=(0.0,
        -12.0, 0.0), axisPoint=(284.88, 12.0, 57.14), instanceList=('SideWeld-1',
        ))
    mdb.models['Model-1'].rootAssembly.rotate(angle=90.0, axisDirection=(0.0, 0.0,
        4.0), axisPoint=(284.88, 0.0, 57.14), instanceList=('SideWeld-1', ))
    del mdb.models['Model-1'].parts['Brace']
    mdb.models['Model-1'].ConstrainedSketch(name='__profile__', sheetSize=200.0)
    mdb.models['Model-1'].sketches['__profile__'].rectangle(point1=(0.0, 0.0),
        point2=(88.9, 88.9))
    mdb.models['Model-1'].sketches['__profile__'].offset(distance=7.94, objectList=
        (mdb.models['Model-1'].sketches['__profile__'].geometry[2],
        mdb.models['Model-1'].sketches['__profile__'].geometry[3],
        mdb.models['Model-1'].sketches['__profile__'].geometry[4],
        mdb.models['Model-1'].sketches['__profile__'].geometry[5]), side=LEFT)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[8], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[7], nearPoint1=(
        31.6611022949219, 82.732536315918), nearPoint2=(79.0807495117188,
        68.9981384277344), radius=7.94)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[7], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[6], nearPoint1=(
        79.7832794189453, 66.1808090209961), nearPoint2=(60.8154144287109,
        10.1866836547852), radius=7.94)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[6], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[9], nearPoint1=(
        60.1128845214844, 8.77803039550781), nearPoint2=(10.2344436645508,
        30.9643783569336), radius=7.94)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[9], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[8], nearPoint1=(
        8.12690734863281, 30.6122131347656), nearPoint2=(20.4208908081055,
        79.5630569458008), radius=7.94)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[3], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[2], nearPoint1=(
        29.9048156738281, 90.8323287963867), nearPoint2=(-1.00577545166016,
        70.4067916870117), radius=15.88)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[2], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[5], nearPoint1=(
        -0.654518127441406, 69.7024612426758), nearPoint2=(8.12690734863281,
        2.43906784057617), radius=15.88)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[5], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[4], nearPoint1=(
        19.3671188354492, 1.03041076660156), nearPoint2=(87.5109100341797,
        22.8646011352539), radius=15.88)
    mdb.models['Model-1'].sketches['__profile__'].FilletByRadius(curve1=
        mdb.models['Model-1'].sketches['__profile__'].geometry[4], curve2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[3], nearPoint1=(
        89.2672119140625, 24.9775848388672), nearPoint2=(66.7867736816406,
        89.0714950561523), radius=15.88)
    mdb.models['Model-1'].Part(dimensionality=THREE_D, name='Brace', type=
        DEFORMABLE_BODY)
    mdb.models['Model-1'].parts['Brace'].BaseSolidExtrude(depth=260.0, sketch=
        mdb.models['Model-1'].sketches['__profile__'])
    del mdb.models['Model-1'].sketches['__profile__']
    mdb.models['Model-1'].ConstrainedSketch(name='__profile__', sheetSize=200.0)
    mdb.models['Model-1'].sketches['__profile__'].ConstructionLine(point1=(0.0,
        -100.0), point2=(0.0, 100.0))
    mdb.models['Model-1'].sketches['__profile__'].FixedConstraint(entity=
        mdb.models['Model-1'].sketches['__profile__'].geometry[2])
    mdb.models['Model-1'].sketches['__profile__'].Line(point1=(15.88, 0.0), point2=
        (15.88, 12.0))
    mdb.models['Model-1'].sketches['__profile__'].VerticalConstraint(addUndoState=
        False, entity=mdb.models['Model-1'].sketches['__profile__'].geometry[3])
    mdb.models['Model-1'].sketches['__profile__'].Line(point1=(15.88, 12.0),
        point2=(19.88, 0.0))
    mdb.models['Model-1'].sketches['__profile__'].Line(point1=(19.88, 0.0), point2=
        (15.88, 0.0))
    mdb.models['Model-1'].sketches['__profile__'].HorizontalConstraint(
        addUndoState=False, entity=
        mdb.models['Model-1'].sketches['__profile__'].geometry[5])
    mdb.models['Model-1'].Part(dimensionality=THREE_D, name='CornerWeld', type=
        DEFORMABLE_BODY)
    mdb.models['Model-1'].parts['CornerWeld'].BaseSolidRevolve(angle=90.0,
        flipRevolveDirection=OFF, sketch=
        mdb.models['Model-1'].sketches['__profile__'])
    del mdb.models['Model-1'].sketches['__profile__']
    mdb.models['Model-1'].parts['CornerWeld'].Set(cells=
        mdb.models['Model-1'].parts['CornerWeld'].cells.getSequenceFromMask((
        '[#1 ]', ), ), name='Set-1')
    mdb.models['Model-1'].parts['CornerWeld'].SectionAssignment(offset=0.0,
        offsetField='', offsetType=MIDDLE_SURFACE, region=
        mdb.models['Model-1'].parts['CornerWeld'].sets['Set-1'], sectionName=
        'Steel', thicknessAssignment=FROM_SECTION)
    mdb.models['Model-1'].parts['Brace'].Set(cells=
        mdb.models['Model-1'].parts['Brace'].cells.getSequenceFromMask(('[#1 ]', ),
        ), name='Set-1')
    mdb.models['Model-1'].parts['Brace'].SectionAssignment(offset=0.0, offsetField=
        '', offsetType=MIDDLE_SURFACE, region=
        mdb.models['Model-1'].parts['Brace'].sets['Set-1'], sectionName='Steel',
        thicknessAssignment=FROM_SECTION)
    mdb.models['Model-1'].parts['SideWeld'].Set(cells=
        mdb.models['Model-1'].parts['SideWeld'].cells.getSequenceFromMask(('[#1 ]',
        ), ), name='Set-1')
    mdb.models['Model-1'].parts['SideWeld'].SectionAssignment(offset=0.0,
        offsetField='', offsetType=MIDDLE_SURFACE, region=
        mdb.models['Model-1'].parts['SideWeld'].sets['Set-1'], sectionName='Steel',
        thicknessAssignment=FROM_SECTION)
    mdb.models['Model-1'].rootAssembly.regenerate()
    mdb.models['Model-1'].rootAssembly.deleteFeatures(('Datum csys-1', 'Brace-1',
        'Chord-1', 'SideWeld-1'))
    mdb.models['Model-1'].rootAssembly.DatumCsysByDefault(CARTESIAN)
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='Brace-1', part=
        mdb.models['Model-1'].parts['Brace'])
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='Chord-1', part=
        mdb.models['Model-1'].parts['Chord'])
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='CornerWeld-1',
        part=mdb.models['Model-1'].parts['CornerWeld'])
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='SideWeld-1',
        part=mdb.models['Model-1'].parts['SideWeld'])
    mdb.models['Model-1'].rootAssembly.instances['Chord-1'].translate(vector=(
        106.68, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1'].translate(vector=(
        286.468, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.instances['SideWeld-1'].translate(vector=(
        306.748, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='Brace-2', part=
        mdb.models['Model-1'].parts['Brace'])
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='CornerWeld-2',
        part=mdb.models['Model-1'].parts['CornerWeld'])
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='SideWeld-2',
        part=mdb.models['Model-1'].parts['SideWeld'])
    mdb.models['Model-1'].rootAssembly.instances['Brace-2'].translate(vector=(
        319.638, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.instances['CornerWeld-2'].translate(vector=(
        410.526, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.instances['SideWeld-2'].translate(vector=(
        430.806, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.DatumPointByCoordinate(coords=(195.58,
        177.8, 525.0))
    mdb.models['Model-1'].rootAssembly.DatumPointByCoordinate(coords=(195.58, 0.0,
        525.0))
    mdb.models['Model-1'].rootAssembly.rotate(angle=90.0, axisDirection=(
        -57.140002, 0.0, 0.0), axisPoint=(392.658001, 80.96, 260.0), instanceList=(
        'Brace-2', 'Brace-1'))
    mdb.models['Model-1'].rootAssembly.DatumPointByCoordinate(coords=(346.088,
        -179.04, 296.51))
    del mdb.models['Model-1'].rootAssembly.features['Datum pt-3']
    mdb.models['Model-1'].rootAssembly.DatumPointByCoordinate(coords=(364.088,
        -179.04, 296.51))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('Brace-2', ),
        vector=(-168.508, 356.84, 228.49))
    mdb.models['Model-1'].rootAssembly.DatumPointByCoordinate(coords=(44.45, 80.96,
        296.51))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('Brace-1', ),
        vector=(151.13, -80.96, 228.49))


    # ----------
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('SideWeld-1', ),
        vector=(-66.718, 177.8, 496.430002))
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='CornerWeld-3',
        part=mdb.models['Model-1'].parts['CornerWeld'])
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='SideWeld-3',
        part=mdb.models['Model-1'].parts['SideWeld'])
    mdb.models['Model-1'].rootAssembly.instances['CornerWeld-3'].translate(vector=(
        436.794, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.instances['SideWeld-3'].translate(vector=(
        457.074, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='CornerWeld-4',
        part=mdb.models['Model-1'].parts['CornerWeld'])
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='SideWeld-4',
        part=mdb.models['Model-1'].parts['SideWeld'])
    mdb.models['Model-1'].rootAssembly.instances['CornerWeld-4'].translate(vector=(
        463.062, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.instances['SideWeld-4'].translate(vector=(
        483.342, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='CornerWeld-5',
        part=mdb.models['Model-1'].parts['CornerWeld'])
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='SideWeld-5',
        part=mdb.models['Model-1'].parts['SideWeld'])
    mdb.models['Model-1'].rootAssembly.instances['CornerWeld-5'].translate(vector=(
        489.33, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.instances['SideWeld-5'].translate(vector=(
        509.61, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.rotate(angle=90.0, axisDirection=(0.0,
        -12.0, 0.0), axisPoint=(430.806, 12.0, 57.14), instanceList=('SideWeld-2',
        ))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('SideWeld-2', ),
        vector=(-263.795998, 177.8, 512.31))


    # ----------
    mdb.models['Model-1'].rootAssembly.rotate(angle=270.0, axisDirection=(0.0,
        -12.0, 0.0), axisPoint=(457.074, 12.0, 57.14), instanceList=('SideWeld-3',
        ))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('SideWeld-3', ),
        vector=(-232.923998, 177.8, 423.41))
    mdb.models['Model-1'].rootAssembly.rotate(angle=180.0, axisDirection=(0.0,
        -12.0, 0.0), axisPoint=(483.342, 12.0, 57.14), instanceList=('SideWeld-4',
        ))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('SideWeld-4', ),
        vector=(-332.212, 177.8, 439.290002))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('CornerWeld-5', ),
        vector=(-265.18, 177.8, 553.570002))
    mdb.models['Model-1'].rootAssembly.rotate(angle=90.0, axisDirection=(0.0,
        -12.0, 0.0), axisPoint=(410.526, 12.0, 15.88), instanceList=(
        'CornerWeld-2', ))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('CornerWeld-2', ),
        vector=(-259.396002, 177.8, 537.69))
    mdb.models['Model-1'].rootAssembly.rotate(angle=180.0, axisDirection=(0.0,
        -12.0, 0.0), axisPoint=(463.062, 12.0, 15.88), instanceList=(
        'CornerWeld-4', ))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('CornerWeld-4', ),
        vector=(-296.052002, 177.8, 464.67))
    mdb.models['Model-1'].rootAssembly.rotate(angle=270.0, axisDirection=(0.0,
        -12.0, 0.0), axisPoint=(436.794, 12.0, 15.88), instanceList=(
        'CornerWeld-3', ))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('CornerWeld-3', ),
        vector=(-196.764, 177.8, 480.549998))
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='CornerWeld-6',
        part=mdb.models['Model-1'].parts['CornerWeld'])
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='SideWeld-6',
        part=mdb.models['Model-1'].parts['SideWeld'])
    mdb.models['Model-1'].rootAssembly.instances['CornerWeld-6'].translate(vector=(
        515.598, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.instances['SideWeld-6'].translate(vector=(
        535.878, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='CornerWeld-7',
        part=mdb.models['Model-1'].parts['CornerWeld'])
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='SideWeld-7',
        part=mdb.models['Model-1'].parts['SideWeld'])
    mdb.models['Model-1'].rootAssembly.instances['CornerWeld-7'].translate(vector=(
        541.866, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.instances['SideWeld-7'].translate(vector=(
        562.146, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='CornerWeld-8',
        part=mdb.models['Model-1'].parts['CornerWeld'])
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='SideWeld-8',
        part=mdb.models['Model-1'].parts['SideWeld'])
    mdb.models['Model-1'].rootAssembly.instances['CornerWeld-8'].translate(vector=(
        568.134, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.instances['SideWeld-8'].translate(vector=(
        588.414, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.rotate(angle=180.0, axisDirection=(4.0, 0.0,
        0.0), axisPoint=(562.146, 0.0, 57.14), instanceList=('SideWeld-5',
        'CornerWeld-6', 'SideWeld-6', 'CornerWeld-7', 'SideWeld-7', 'CornerWeld-8',
        'SideWeld-8', 'CornerWeld-1'))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('CornerWeld-1', ),
        vector=(-62.318, 0.0, 382.149998))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('SideWeld-5', ),
        vector=(-269.58, 0.0, 439.290002))
    mdb.models['Model-1'].rootAssembly.deleteFeatures(('CornerWeld-1',
        'SideWeld-5'))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('SideWeld-6', ),
        vector=(-295.848, 0.0, 439.289998))
    mdb.models['Model-1'].rootAssembly.rotate(angle=90.0, axisDirection=(0.0, 12.0,
        0.0), axisPoint=(562.146, -12.0, 114.28), instanceList=('SideWeld-7', ))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('SideWeld-7', ),
        vector=(-337.995998, 0.0, 366.27))
    mdb.models['Model-1'].rootAssembly.rotate(angle=180.0, axisDirection=(0.0,
        12.0, 0.0), axisPoint=(588.414, -12.0, 114.28), instanceList=('SideWeld-8',
        ))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('SideWeld-8', ),
        vector=(-437.284, 0.0, 382.150002))
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='CornerWeld-1',
        part=mdb.models['Model-1'].parts['CornerWeld'])
    mdb.models['Model-1'].rootAssembly.Instance(dependent=ON, name='SideWeld-5',
        part=mdb.models['Model-1'].parts['SideWeld'])
    mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1'].translate(vector=(
        590.002, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.instances['SideWeld-5'].translate(vector=(
        610.282, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.rotate(angle=180.0, axisDirection=(4.0, 0.0,
        0.0), axisPoint=(610.282, 0.0, 57.14), instanceList=('CornerWeld-1',
        'SideWeld-5'))
    mdb.models['Model-1'].rootAssembly.rotate(angle=270.0, axisDirection=(0.0,
        12.0, 0.0), axisPoint=(610.282, -12.0, 114.28), instanceList=('SideWeld-5',
        ))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('SideWeld-5', ),
        vector=(-443.271998, 0.0, 455.17))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('CornerWeld-1', ),
        vector=(-365.852, 0.0, 382.149998))
    mdb.models['Model-1'].rootAssembly.rotate(angle=90.0, axisDirection=(0.0, 12.0,
        0.0), axisPoint=(584.014, -12.0, 114.28), instanceList=('CornerWeld-8', ))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('CornerWeld-8', ),
        vector=(-417.004002, 0.0, 366.27))
    mdb.models['Model-1'].rootAssembly.rotate(angle=180.0, axisDirection=(0.0,
        12.0, 0.0), axisPoint=(557.746, -12.0, 114.28), instanceList=(
        'CornerWeld-7', ))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('CornerWeld-7', ),
        vector=(-406.616, 0.0, 439.290002))
    mdb.models['Model-1'].rootAssembly.rotate(angle=270.0, axisDirection=(0.0,
        12.0, 0.0), axisPoint=(531.478, -12.0, 114.28), instanceList=(
        'CornerWeld-6', ))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('CornerWeld-6', ),
        vector=(-307.328, 0.0, 455.170002))


    # ----------
    del mdb.models['Model-1'].rootAssembly.features['SideWeld-2']
    del mdb.models['Model-1'].rootAssembly.features['CornerWeld-5']
    del mdb.models['Model-1'].rootAssembly.features['SideWeld-1']
    del mdb.models['Model-1'].rootAssembly.features['CornerWeld-3']
    del mdb.models['Model-1'].rootAssembly.features['CornerWeld-2']
    del mdb.models['Model-1'].rootAssembly.features['SideWeld-4']
    del mdb.models['Model-1'].rootAssembly.features['CornerWeld-4']
    del mdb.models['Model-1'].rootAssembly.features['SideWeld-3']
    del mdb.models['Model-1'].rootAssembly.features['CornerWeld-1']
    del mdb.models['Model-1'].rootAssembly.features['SideWeld-7']
    del mdb.models['Model-1'].rootAssembly.features['SideWeld-6']
    del mdb.models['Model-1'].rootAssembly.features['CornerWeld-8']
    del mdb.models['Model-1'].rootAssembly.features['CornerWeld-6']
    del mdb.models['Model-1'].rootAssembly.features['SideWeld-5']
    del mdb.models['Model-1'].rootAssembly.features['CornerWeld-7']
    del mdb.models['Model-1'].rootAssembly.features['SideWeld-8']


    # ----------
    mdb.models['Model-1'].StaticStep(initialInc=0.2, minInc=1e-15, name='Step-1',
        nlgeom=ON, previous='Initial')
    mdb.models['Model-1'].rootAssembly.makeIndependent(instances=(
        mdb.models['Model-1'].rootAssembly.instances['Brace-1'],
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'],
        mdb.models['Model-1'].rootAssembly.instances['Brace-2']))
    mdb.models['Model-1'].rootAssembly.seedPartInstance(deviationFactor=0.1,
        minSizeFactor=0.1, regions=(
        mdb.models['Model-1'].rootAssembly.instances['Brace-2'], ), size=13.0)
    mdb.models['Model-1'].rootAssembly.seedPartInstance(deviationFactor=0.1,
        minSizeFactor=0.1, regions=(
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'], ), size=53.0)
    mdb.models['Model-1'].rootAssembly.seedPartInstance(deviationFactor=0.1,
        minSizeFactor=0.1, regions=(
        mdb.models['Model-1'].rootAssembly.instances['Brace-1'], ), size=13.0)
    mdb.models['Model-1'].rootAssembly.generateMesh(regions=(
        mdb.models['Model-1'].rootAssembly.instances['Brace-1'],
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'],
        mdb.models['Model-1'].rootAssembly.instances['Brace-2']))
    mdb.models['Model-1'].rootAssembly.DatumPlaneByPrincipalPlane(offset=600.0,
        principalPlane=XYPLANE)
    mdb.models['Model-1'].rootAssembly.DatumPlaneByPrincipalPlane(offset=430.0,
        principalPlane=XYPLANE)
    del mdb.models['Model-1'].rootAssembly.features['Datum plane-1']
    del mdb.models['Model-1'].rootAssembly.features['Datum plane-2']
    mdb.models['Model-1'].rootAssembly.DatumPlaneByPrincipalPlane(offset=575.0,
        principalPlane=XYPLANE)
    del mdb.models['Model-1'].rootAssembly.features['Datum plane-1']
    mdb.models['Model-1'].rootAssembly.DatumPlaneByPrincipalPlane(offset=619.45,
        principalPlane=XYPLANE)
    mdb.models['Model-1'].rootAssembly.DatumPlaneByPrincipalPlane(offset=430.55,
        principalPlane=XYPLANE)
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].cells.getSequenceFromMask(
        ('[#1 ]', ), ))
    mdb.models['Model-1'].rootAssembly.PartitionCellByDatumPlane(cells=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].cells.getSequenceFromMask(
        ('[#1 ]', ), ), datumPlane=mdb.models['Model-1'].rootAssembly.datums[63])
    mdb.models['Model-1'].rootAssembly.PartitionCellByDatumPlane(cells=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].cells.getSequenceFromMask(
        ('[#1 ]', ), ), datumPlane=mdb.models['Model-1'].rootAssembly.datums[62])
    mdb.models['Model-1'].rootAssembly.DatumPlaneByPrincipalPlane(offset=227.8,
        principalPlane=XZPLANE)
    mdb.models['Model-1'].rootAssembly.DatumPlaneByPrincipalPlane(offset=-50.0,
        principalPlane=XZPLANE)
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Brace-2'].cells.getSequenceFromMask(
        ('[#1 ]', ), ))
    mdb.models['Model-1'].rootAssembly.PartitionCellByDatumPlane(cells=
        mdb.models['Model-1'].rootAssembly.instances['Brace-2'].cells.getSequenceFromMask(
        ('[#1 ]', ), ), datumPlane=mdb.models['Model-1'].rootAssembly.datums[66])
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Brace-1'].cells.getSequenceFromMask(
        ('[#1 ]', ), ))
    mdb.models['Model-1'].rootAssembly.PartitionCellByDatumPlane(cells=
        mdb.models['Model-1'].rootAssembly.instances['Brace-1'].cells.getSequenceFromMask(
        ('[#1 ]', ), ), datumPlane=mdb.models['Model-1'].rootAssembly.datums[67])
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Brace-2'].edges.getSequenceFromMask(
        mask=('[#40000 #4000000 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['Brace-1'].edges.getSequenceFromMask(
        mask=('[#40000000 #100000 #1 ]', ), ), minSizeFactor=0.1, size=2.0)
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Brace-1'].edges.getSequenceFromMask(
        mask=('[#50000 #4000000 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['Brace-2'].edges.getSequenceFromMask(
        mask=('[#280000 #40000000 ]', ), ), number=16)
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].edges.getSequenceFromMask(
        ('[#11080000 #1 #0 #30 ]', ), ), minSizeFactor=0.1, size=2.0)
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Brace-1'].edges.getSequenceFromMask(
        mask=('[#20000 #808000 #200 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['Brace-2'].edges.getSequenceFromMask(
        mask=('[#800800 #20020000 #8802 ]', ), ), number=8)
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].edges.getSequenceFromMask(
        ('[#20100080 #20000000 #41002100 #1000 ]', ), ), number=8)
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].edges.getSequenceFromMask(
        ('[#a000040 #400000 #50 ]', ), ), minSizeFactor=0.1, size=4.0)
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Brace-1'].edges.getSequenceFromMask(
        mask=('[#8000040 #2000000 #80 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['Brace-2'].edges.getSequenceFromMask(
        mask=('[#8000040 #2000000 ]', ), ), minSizeFactor=0.1, size=4.0)
    mdb.models['Model-1'].rootAssembly.generateMesh(regions=(
        mdb.models['Model-1'].rootAssembly.instances['Brace-1'],
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'],
        mdb.models['Model-1'].rootAssembly.instances['Brace-2']))
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].cells.getSequenceFromMask(
        ('[#7 ]', ), ))
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].edges.getSequenceFromMask(
        ('[#20010 #a #8010801 #2008 ]', ), ), number=6)
    mdb.models['Model-1'].rootAssembly.generateMesh(regions=(
        mdb.models['Model-1'].rootAssembly.instances['Brace-1'],
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'],
        mdb.models['Model-1'].rootAssembly.instances['Brace-2']))
    mdb.models['Model-1'].rootAssembly.Surface(name='m_Surf-1', side1Faces=
        mdb.models['Model-1'].rootAssembly.instances['Brace-2'].faces.getSequenceFromMask(
        ('[#0 #4 ]', ), ))
    mdb.models['Model-1'].rootAssembly.Surface(name='s_Surf-1', side1Faces=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].faces.getSequenceFromMask(
        ('[#10 ]', ), ))
    mdb.models['Model-1'].Tie(adjust=ON, master=
        mdb.models['Model-1'].rootAssembly.surfaces['m_Surf-1'], name='brace-chord'
        , positionToleranceMethod=COMPUTED, slave=
        mdb.models['Model-1'].rootAssembly.surfaces['s_Surf-1'], thickness=ON,
        tieRotations=ON)
    mdb.models['Model-1'].rootAssembly.Surface(name='m_Surf-3', side1Faces=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].faces.getSequenceFromMask(
        ('[#0 #100 ]', ), ))
    mdb.models['Model-1'].rootAssembly.Surface(name='s_Surf-3', side1Faces=
        mdb.models['Model-1'].rootAssembly.instances['Brace-1'].faces.getSequenceFromMask(
        ('[#0 #2 ]', ), ))
    mdb.models['Model-1'].Tie(adjust=ON, master=
        mdb.models['Model-1'].rootAssembly.surfaces['m_Surf-3'], name='chord-brace'
        , positionToleranceMethod=COMPUTED, slave=
        mdb.models['Model-1'].rootAssembly.surfaces['s_Surf-3'], thickness=ON,
        tieRotations=ON)
    mdb.models['Model-1'].rootAssembly.Surface(name='Surf-5', side1Faces=
        mdb.models['Model-1'].rootAssembly.instances['Brace-2'].faces.getSequenceFromMask(
        ('[#0 #2 ]', ), ))
    mdb.models['Model-1'].Pressure(amplitude=UNSET, createStepName='Step-1',
        distributionType=TOTAL_FORCE, field='', magnitude=-72.3, name='Load-1',
        region=mdb.models['Model-1'].rootAssembly.surfaces['Surf-5'])
    del mdb.models['Model-1'].loads['Load-1']
    mdb.models['Model-1'].rootAssembly.Surface(name='Surf-6', side1Faces=
        mdb.models['Model-1'].rootAssembly.instances['Brace-2'].faces.getSequenceFromMask(
        ('[#0 #2 ]', ), ))
    mdb.models['Model-1'].Pressure(amplitude=UNSET, createStepName='Step-1',
        distributionType=TOTAL_FORCE, field='', magnitude=72.3, name='Load-1',
        region=mdb.models['Model-1'].rootAssembly.surfaces['Surf-6'])
    del mdb.models['Model-1'].loads['Load-1']
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Brace-2'].cells.getSequenceFromMask(
        ('[#1 ]', ), ))
    mdb.models['Model-1'].rootAssembly.deleteSeeds(regions=
        mdb.models['Model-1'].rootAssembly.instances['Brace-2'].edges.getSequenceFromMask(
        ('[#800000 #20020000 #8802 ]', ), ))
    mdb.models['Model-1'].rootAssembly.generateMesh(regions=(
        mdb.models['Model-1'].rootAssembly.instances['Brace-2'], ))
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Brace-2'].cells.getSequenceFromMask(
        ('[#1 ]', ), ))
    mdb.models['Model-1'].rootAssembly.deleteSeeds(regions=
        mdb.models['Model-1'].rootAssembly.instances['Brace-2'].edges.getSequenceFromMask(
        ('[#8000000 ]', ), ))
    mdb.models['Model-1'].rootAssembly.generateMesh(regions=(
        mdb.models['Model-1'].rootAssembly.instances['Brace-2'], ))


    # ----------
    mdb.models['Model-1'].rootAssembly.Surface(name='Surf-7', side1Faces=
        mdb.models['Model-1'].rootAssembly.instances['Brace-2'].faces.getSequenceFromMask(
        ('[#0 #2 ]', ), ))
    mdb.models['Model-1'].Pressure(amplitude=UNSET, createStepName='Step-1',
        distributionType=TOTAL_FORCE, field='', magnitude=72.3, name='Load-1',
        region=mdb.models['Model-1'].rootAssembly.surfaces['Surf-7'])
    del mdb.models['Model-1'].loads['Load-1']
    mdb.models['Model-1'].rootAssembly.DatumPointByMidPoint(point1=
        mdb.models['Model-1'].rootAssembly.instances['Brace-2'].InterestingPoint(
        mdb.models['Model-1'].rootAssembly.instances['Brace-2'].edges[77], MIDDLE),
        point2=
        mdb.models['Model-1'].rootAssembly.instances['Brace-2'].InterestingPoint(
        mdb.models['Model-1'].rootAssembly.instances['Brace-2'].edges[45], MIDDLE))
    mdb.models['Model-1'].rootAssembly.DatumPointByMidPoint(point1=
        mdb.models['Model-1'].rootAssembly.instances['Brace-1'].InterestingPoint(
        mdb.models['Model-1'].rootAssembly.instances['Brace-1'].edges[43], MIDDLE),
        point2=
        mdb.models['Model-1'].rootAssembly.instances['Brace-1'].InterestingPoint(
        mdb.models['Model-1'].rootAssembly.instances['Brace-1'].edges[71], MIDDLE))


    # ----------
    mdb.saveAs(pathName='D:/Thesis/Abaqus Models/X-178x89-NoHole/X178x891tie+weld.cae')
    mdb.models['Model-1'].parts['Chord'].PartitionCellByPlanePointNormal(cells=
        mdb.models['Model-1'].parts['Chord'].cells.getSequenceFromMask(('[#1 ]', ),
        ), normal=mdb.models['Model-1'].parts['Chord'].edges[8], point=
        mdb.models['Model-1'].parts['Chord'].InterestingPoint(
        mdb.models['Model-1'].parts['Chord'].edges[8], MIDDLE))
    mdb.models['Model-1'].parts['Chord'].RemoveFaces(deleteCells=False, faceList=
        mdb.models['Model-1'].parts['Chord'].faces.getSequenceFromMask(mask=(
        '[#e1e15554 #3 ]', ), ))


    # ----------
    mdb.models['Model-1'].rootAssembly.regenerate()
    #* FeatureError: Regeneration failed
    mdb.models['Model-1'].parts['Brace'].PartitionCellByPlanePointNormal(cells=
        mdb.models['Model-1'].parts['Brace'].cells.getSequenceFromMask(('[#1 ]', ),
        ), normal=mdb.models['Model-1'].parts['Brace'].edges[13], point=
        mdb.models['Model-1'].parts['Brace'].InterestingPoint(
        mdb.models['Model-1'].parts['Brace'].edges[13], MIDDLE))
    mdb.models['Model-1'].parts['Brace'].RemoveFaces(deleteCells=False, faceList=
        mdb.models['Model-1'].parts['Brace'].faces.getSequenceFromMask(mask=(
        '[#1001e80 ]', ), ))
    mdb.models['Model-1'].parts['Brace'].RemoveFaces(deleteCells=False, faceList=
        mdb.models['Model-1'].parts['Brace'].faces.getSequenceFromMask(mask=(
        '[#70c8 ]', ), ))


    # ----------
    mdb.models['Model-1'].rootAssembly.regenerate()
    #* FeatureError: Regeneration failed
    mdb.models['Model-1'].rootAssembly.deleteFeatures(('Datum plane-1',
        'Datum plane-2', 'Datum plane-3', 'Datum plane-4', 'Datum csys-1',
        'Datum pt-1', 'Datum pt-2', 'Datum pt-3', 'Datum pt-4', 'Partition cell-4',
        'Brace-1', 'Partition cell-1', 'Chord-1', 'Partition cell-3', 'Brace-2'))
    mdb.models['Model-1'].rootAssembly.DatumCsysByDefault(CARTESIAN)
    mdb.models['Model-1'].rootAssembly.Instance(dependent=OFF, name='Brace-1',
        part=mdb.models['Model-1'].parts['Brace'])
    mdb.models['Model-1'].rootAssembly.Instance(dependent=OFF, name='Chord-1',
        part=mdb.models['Model-1'].parts['Chord'])
    mdb.models['Model-1'].rootAssembly.Instance(dependent=OFF, name='CornerWeld-1',
        part=mdb.models['Model-1'].parts['CornerWeld'])
    mdb.models['Model-1'].rootAssembly.Instance(dependent=OFF, name='SideWeld-1',
        part=mdb.models['Model-1'].parts['SideWeld'])
    mdb.models['Model-1'].rootAssembly.instances['Chord-1'].translate(vector=(
        106.68, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1'].translate(vector=(
        286.468, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.instances['SideWeld-1'].translate(vector=(
        306.748, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.rotate(angle=90.0, axisDirection=(57.140003,
        0.0, 0.0), axisPoint=(15.879998, 0.0, 260.0), instanceList=('Brace-1', ))
    mdb.models['Model-1'].rootAssembly.DatumPointByMidPoint(point1=
        mdb.models['Model-1'].rootAssembly.instances['Brace-1'].vertices[7],
        point2=mdb.models['Model-1'].rootAssembly.instances['Brace-1'].vertices[3])
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('Brace-1', ),
        vector=(151.13, 177.8, 220.55))
    mdb.models['Model-1'].rootAssembly.rotate(angle=90.0, axisDirection=(0.0,
        -12.0, 0.0), axisPoint=(286.468, 12.0, 15.88), instanceList=(
        'CornerWeld-1', ))
    mdb.models['Model-1'].rootAssembly.rotate(angle=90.0, axisDirection=(0.0,
        -12.0, 0.0), axisPoint=(286.468, 12.0, 15.88), instanceList=(
        'CornerWeld-1', ))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('CornerWeld-1', ),
        vector=(-119.458002, 177.8, 464.67))
    mdb.models['Model-1'].rootAssembly.LinearInstancePattern(direction1=(1.0, 0.0,
        0.0), direction2=(0.0, 1.0, 0.0), instanceList=('CornerWeld-1', ), number1=
        1, number2=4, spacing1=19.88, spacing2=12.0)
    mdb.models['Model-1'].rootAssembly.rotate(angle=90.0, axisDirection=(0.0,
        -12.0, 0.0), axisPoint=(167.009998, 225.8, 480.55), instanceList=(
        'CornerWeld-1-lin-1-4', ))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=(
        'CornerWeld-1-lin-1-4', ), vector=(73.020002, -36.0, 15.879998))
    mdb.models['Model-1'].rootAssembly.rotate(angle=180.0, axisDirection=(0.0, 0.0,
        4.0), axisPoint=(167.009998, 201.8, 476.55), instanceList=(
        'CornerWeld-1-lin-1-3', 'CornerWeld-1-lin-1-2'))
    mdb.models['Model-1'].rootAssembly.deleteFeatures(('CornerWeld-1-lin-1-2',
        'CornerWeld-1-lin-1-3'))
    mdb.models['Model-1'].rootAssembly.rotate(angle=90.0, axisDirection=(0.0,
        -12.0, 0.0), axisPoint=(306.748, 12.0, 57.14), instanceList=('SideWeld-1',
        ))
    mdb.models['Model-1'].rootAssembly.rotate(angle=180.0, axisDirection=(0.0,
        -12.0, 0.0), axisPoint=(363.888, 12.0, 57.14), instanceList=('SideWeld-1',
        ))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('SideWeld-1', ),
        vector=(-196.878, 177.8, 423.41))
    mdb.models['Model-1'].ConstrainedSketch(name='__profile__', sheetSize=200.0)
    mdb.models['Model-1'].sketches['__profile__'].Line(point1=(0.0, 0.0), point2=(
        0.0, 12.0))
    mdb.models['Model-1'].sketches['__profile__'].VerticalConstraint(addUndoState=
        False, entity=mdb.models['Model-1'].sketches['__profile__'].geometry[2])
    mdb.models['Model-1'].sketches['__profile__'].Line(point1=(0.0, 12.0), point2=(
        4.0, 0.0))
    mdb.models['Model-1'].sketches['__profile__'].Line(point1=(4.0, 0.0), point2=(
        0.0, 0.0))
    mdb.models['Model-1'].sketches['__profile__'].HorizontalConstraint(
        addUndoState=False, entity=
        mdb.models['Model-1'].sketches['__profile__'].geometry[4])
    mdb.models['Model-1'].Part(dimensionality=THREE_D, name='HalfSideWeld', type=
        DEFORMABLE_BODY)
    mdb.models['Model-1'].parts['HalfSideWeld'].BaseSolidExtrude(depth=28.57,
        sketch=mdb.models['Model-1'].sketches['__profile__'])
    del mdb.models['Model-1'].sketches['__profile__']
    mdb.models['Model-1'].parts['HalfSideWeld'].Set(cells=
        mdb.models['Model-1'].parts['HalfSideWeld'].cells.getSequenceFromMask((
        '[#1 ]', ), ), name='Set-1')
    mdb.models['Model-1'].parts['HalfSideWeld'].SectionAssignment(offset=0.0,
        offsetField='', offsetType=MIDDLE_SURFACE, region=
        mdb.models['Model-1'].parts['HalfSideWeld'].sets['Set-1'], sectionName=
        'Steel', thicknessAssignment=FROM_SECTION)
    mdb.models['Model-1'].rootAssembly.Instance(dependent=OFF, name=
        'HalfSideWeld-1', part=mdb.models['Model-1'].parts['HalfSideWeld'])
    mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1'].translate(
        vector=(284.88, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.LinearInstancePattern(direction1=(1.0, 0.0,
        0.0), direction2=(0.0, 1.0, 0.0), instanceList=('HalfSideWeld-1', ),
        number1=1, number2=2, spacing1=4.0, spacing2=12.0)
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('HalfSideWeld-1', ),
        vector=(-44.85, 177.8, 496.43))
    mdb.models['Model-1'].rootAssembly.rotate(angle=180.0, axisDirection=(0.0,
        -12.0, 0.0), axisPoint=(284.88, 24.0, 28.57), instanceList=(
        'HalfSideWeld-1-lin-1-2', ))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=(
        'HalfSideWeld-1-lin-1-2', ), vector=(-133.75, 165.8, 467.86))


    # ----------
    mdb.models['Model-1'].rootAssembly.LinearInstancePattern(direction1=(1.0, 0.0,
        0.0), direction2=(0.0, -1.0, 0.0), instanceList=('Brace-1',
        'HalfSideWeld-1', 'CornerWeld-1-lin-1-4', 'SideWeld-1', 'CornerWeld-1',
        'HalfSideWeld-1-lin-1-2'), number1=1, number2=2, spacing1=96.9, spacing2=
        460.0)
    mdb.models['Model-1'].rootAssembly.rotate(angle=180.0, axisDirection=(11.94,
        0.0, 0.0), axisPoint=(232.09, -282.2, 525.0), instanceList=(
        'Brace-1-lin-1-2', 'HalfSideWeld-1-lin-1-2-1',
        'HalfSideWeld-1-lin-1-2-lin-1-2', 'CornerWeld-1-lin-1-4-lin-1-2',
        'SideWeld-1-lin-1-2', 'CornerWeld-1-lin-1-2'))
    mdb.models['Model-1'].rootAssembly.rotate(angle=180.0, axisDirection=(0.0,
        130.0, 0.0), axisPoint=(151.13, -542.2, 553.570002), instanceList=(
        'Brace-1-lin-1-2', 'CornerWeld-1-lin-1-4-lin-1-2', 'SideWeld-1-lin-1-2'))
    mdb.models['Model-1'].rootAssembly.deleteFeatures(('CornerWeld-1',
        'CornerWeld-1-lin-1-4', 'CornerWeld-1-lin-1-4-lin-1-2',
        'CornerWeld-1-lin-1-2', 'Brace-1-lin-1-2', 'HalfSideWeld-1-lin-1-2-1',
        'HalfSideWeld-1-lin-1-2-lin-1-2', 'SideWeld-1-lin-1-2'))
    mdb.models['Model-1'].rootAssembly.Instance(dependent=OFF, name='CornerWeld-1',
        part=mdb.models['Model-1'].parts['CornerWeld'])
    mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1'].translate(vector=(
        286.468, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.Instance(dependent=OFF, name='CornerWeld-2',
        part=mdb.models['Model-1'].parts['CornerWeld'])
    mdb.models['Model-1'].rootAssembly.instances['CornerWeld-2'].translate(vector=(
        308.336, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.rotate(angle=180.0, axisDirection=(0.0,
        12.0, 0.0), axisPoint=(324.216, 0.0, 0.0), instanceList=('CornerWeld-2', ))
    del mdb.models['Model-1'].rootAssembly.features['CornerWeld-1']
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('CornerWeld-2', ),
        vector=(-173.086, 177.8, 496.43))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('CornerWeld-2', ),
        vector=(39.798856, 0.0, -4.651144))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('CornerWeld-2', ),
        vector=(-39.798858, 0.0, 4.651144))
    mdb.models['Model-1'].ConstrainedSketch(name='__profile__', sheetSize=200.0)
    mdb.models['Model-1'].sketches['__profile__'].ArcByCenterEnds(center=(0.0, 0.0)
        , direction=CLOCKWISE, point1=(15.88, 0.0), point2=(0.0, -15.88))
    mdb.models['Model-1'].sketches['__profile__'].Line(point1=(0.0, -15.88),
        point2=(-57.14, -15.88))
    mdb.models['Model-1'].sketches['__profile__'].HorizontalConstraint(
        addUndoState=False, entity=
        mdb.models['Model-1'].sketches['__profile__'].geometry[3])
    mdb.models['Model-1'].sketches['__profile__'].TangentConstraint(addUndoState=
        False, entity1=mdb.models['Model-1'].sketches['__profile__'].geometry[2],
        entity2=mdb.models['Model-1'].sketches['__profile__'].geometry[3])
    mdb.models['Model-1'].sketches['__profile__'].ArcByCenterEnds(center=(-57.14,
        0.0), direction=CLOCKWISE, point1=(-57.14, -15.88), point2=(-73.02, 0.0))
    mdb.models['Model-1'].sketches['__profile__'].Line(point1=(-73.02, 0.0),
        point2=(-73.02, 57.14))
    mdb.models['Model-1'].sketches['__profile__'].VerticalConstraint(addUndoState=
        False, entity=mdb.models['Model-1'].sketches['__profile__'].geometry[5])
    mdb.models['Model-1'].sketches['__profile__'].TangentConstraint(addUndoState=
        False, entity1=mdb.models['Model-1'].sketches['__profile__'].geometry[4],
        entity2=mdb.models['Model-1'].sketches['__profile__'].geometry[5])
    mdb.models['Model-1'].sketches['__profile__'].ArcByCenterEnds(center=(-57.14,
        57.14), direction=CLOCKWISE, point1=(-73.02, 57.14), point2=(-57.14,
        73.02))
    mdb.models['Model-1'].sketches['__profile__'].Line(point1=(-57.14, 73.02),
        point2=(0.0, 73.02))
    mdb.models['Model-1'].sketches['__profile__'].HorizontalConstraint(
        addUndoState=False, entity=
        mdb.models['Model-1'].sketches['__profile__'].geometry[7])
    mdb.models['Model-1'].sketches['__profile__'].TangentConstraint(addUndoState=
        False, entity1=mdb.models['Model-1'].sketches['__profile__'].geometry[6],
        entity2=mdb.models['Model-1'].sketches['__profile__'].geometry[7])
    mdb.models['Model-1'].sketches['__profile__'].Line(point1=(15.88, 0.0), point2=
        (15.88, 57.14))
    mdb.models['Model-1'].sketches['__profile__'].VerticalConstraint(addUndoState=
        False, entity=mdb.models['Model-1'].sketches['__profile__'].geometry[8])
    mdb.models['Model-1'].sketches['__profile__'].TangentConstraint(addUndoState=
        False, entity1=mdb.models['Model-1'].sketches['__profile__'].geometry[2],
        entity2=mdb.models['Model-1'].sketches['__profile__'].geometry[8])
    mdb.models['Model-1'].sketches['__profile__'].ArcByCenterEnds(center=(0.0,
        57.14), direction=COUNTERCLOCKWISE, point1=(15.88, 57.14), point2=(0.0,
        73.02))
    mdb.models['Model-1'].sketches['__profile__'].offset(distance=7.94, objectList=
        (mdb.models['Model-1'].sketches['__profile__'].geometry[2],
        mdb.models['Model-1'].sketches['__profile__'].geometry[3],
        mdb.models['Model-1'].sketches['__profile__'].geometry[4],
        mdb.models['Model-1'].sketches['__profile__'].geometry[5],
        mdb.models['Model-1'].sketches['__profile__'].geometry[6],
        mdb.models['Model-1'].sketches['__profile__'].geometry[7],
        mdb.models['Model-1'].sketches['__profile__'].geometry[8],
        mdb.models['Model-1'].sketches['__profile__'].geometry[9]), side=LEFT)
    mdb.models['Model-1'].Part(dimensionality=THREE_D, name='Brace2', type=
        DEFORMABLE_BODY)
    mdb.models['Model-1'].parts['Brace2'].BaseSolidExtrude(depth=260.0, sketch=
        mdb.models['Model-1'].sketches['__profile__'])
    del mdb.models['Model-1'].sketches['__profile__']
    mdb.models['Model-1'].parts['Brace2'].Set(cells=
        mdb.models['Model-1'].parts['Brace2'].cells.getSequenceFromMask(('[#1 ]',
        ), ), name='Set-1')
    mdb.models['Model-1'].parts['Brace2'].SectionAssignment(offset=0.0,
        offsetField='', offsetType=MIDDLE_SURFACE, region=
        mdb.models['Model-1'].parts['Brace2'].sets['Set-1'], sectionName='Steel',
        thicknessAssignment=FROM_SECTION)
    mdb.models['Model-1'].parts['Brace2'].PartitionCellByPlanePointNormal(cells=
        mdb.models['Model-1'].parts['Brace2'].cells.getSequenceFromMask(('[#1 ]',
        ), ), normal=mdb.models['Model-1'].parts['Brace2'].edges[22], point=
        mdb.models['Model-1'].parts['Brace2'].InterestingPoint(
        mdb.models['Model-1'].parts['Brace2'].edges[22], MIDDLE))
    mdb.models['Model-1'].parts['Brace2'].RemoveFaces(deleteCells=False, faceList=
        mdb.models['Model-1'].parts['Brace2'].faces.getSequenceFromMask(mask=(
        '[#100f080 ]', ), ))
    mdb.models['Model-1'].parts['Brace2'].RemoveFaces(deleteCells=False, faceList=
        mdb.models['Model-1'].parts['Brace2'].faces.getSequenceFromMask(mask=(
        '[#7448 ]', ), ))


    # ----------
    mdb.models['Model-1'].rootAssembly.Instance(dependent=OFF, name='Brace2-1',
        part=mdb.models['Model-1'].parts['Brace2'])
    mdb.models['Model-1'].rootAssembly.instances['Brace2-1'].translate(vector=(
        366.39, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.rotate(angle=90.0, axisDirection=(57.14,
        0.0, 0.0), axisPoint=(309.25, -15.88, 260.0), instanceList=('Brace2-1', ))
    mdb.models['Model-1'].rootAssembly.deleteFeatures(('CornerWeld-2', 'Brace-1'))
    mdb.models['Model-1'].rootAssembly.DatumPointByMidPoint(point1=
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1'].vertices[7],
        point2=
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1'].vertices[2])
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('Brace2-1', ),
        vector=(-142.24, 193.68, 220.55))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('HalfSideWeld-1', ),
        vector=(0.0, 130.0, 0.0))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('HalfSideWeld-1', ),
        vector=(0.0, -130.0, 0.0))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=(
        'HalfSideWeld-1-lin-1-2', ), vector=(0.0, 130.0, 0.0))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=(
        'HalfSideWeld-1-lin-1-2', ), vector=(0.0, -130.0, 0.0))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('SideWeld-1', ),
        vector=(0.0, 130.0, 0.0))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('SideWeld-1', ),
        vector=(0.0, -130.0, 0.0))
    mdb.models['Model-1'].rootAssembly.Instance(dependent=OFF, name='CornerWeld-1',
        part=mdb.models['Model-1'].parts['CornerWeld'])
    mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1'].translate(vector=(
        286.468, 0.0, 0.0))
    mdb.models['Model-1'].rootAssembly.rotate(angle=180.0, axisDirection=(0.0,
        12.0, 0.0), axisPoint=(286.468, 0.0, 15.88), instanceList=('CornerWeld-1',
        ))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('CornerWeld-1', ),
        vector=(-119.458, 177.8, 464.67))
    mdb.models['Model-1'].rootAssembly.LinearInstancePattern(direction1=(1.0, 0.0,
        0.0), direction2=(0.0, -1.0, 0.0), instanceList=('CornerWeld-1', ),
        number1=2, number2=1, spacing1=19.88, spacing2=12.0)
    mdb.models['Model-1'].rootAssembly.rotate(angle=90.0, axisDirection=(0.0,
        -12.0, 0.0), axisPoint=(171.01, 189.8, 496.43), instanceList=(
        'CornerWeld-1-lin-2-1', ))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=(
        'CornerWeld-1-lin-2-1', ), vector=(53.14, 0.0, -15.88))
    mdb.models['Model-1'].rootAssembly.LinearInstancePattern(direction1=(1.0, 0.0,
        0.0), direction2=(0.0, -1.0, 0.0), instanceList=('Brace2-1',
        'HalfSideWeld-1', 'CornerWeld-1-lin-2-1', 'HalfSideWeld-1-lin-1-2',
        'SideWeld-1', 'CornerWeld-1'), number1=2, number2=1, spacing1=230.0,
        spacing2=260.0)
    mdb.models['Model-1'].rootAssembly.rotate(angle=180.0, axisDirection=(-57.14,
        0.0, 0.0), axisPoint=(454.15, 177.8, 488.49), instanceList=(
        'Brace2-1-lin-2-1', 'HalfSideWeld-1-lin-2-1',
        'CornerWeld-1-lin-2-1-lin-2-1', 'SideWeld-1-lin-2-1',
        'CornerWeld-1-lin-2-1-1', 'HalfSideWeld-1-lin-1-2-lin-2-1'))
    mdb.models['Model-1'].rootAssembly.DatumPointByMidPoint(point1=
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1-lin-2-1'].vertices[2]
        , point2=
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1-lin-2-1'].vertices[7])
    mdb.models['Model-1'].rootAssembly.rotate(angle=180.0, axisDirection=(0.0,
        130.0, 0.0), axisPoint=(389.07, -82.2, 451.98), instanceList=(
        'Brace2-1-lin-2-1', 'HalfSideWeld-1-lin-2-1',
        'HalfSideWeld-1-lin-1-2-lin-2-1', 'CornerWeld-1-lin-2-1-lin-2-1',
        'SideWeld-1-lin-2-1', 'CornerWeld-1-lin-2-1-1'))
    mdb.models['Model-1'].rootAssembly.translate(instanceList=('Brace2-1-lin-2-1',
        'HalfSideWeld-1-lin-1-2-lin-2-1', 'CornerWeld-1-lin-2-1-1',
        'SideWeld-1-lin-2-1', 'CornerWeld-1-lin-2-1-lin-2-1',
        'HalfSideWeld-1-lin-2-1'), vector=(-156.98, -177.8, 73.02))


    # ----------
    mdb.models['Model-1'].rootAssembly.DatumPlaneByPrincipalPlane(offset=194.98,
        principalPlane=XZPLANE)
    mdb.models['Model-1'].rootAssembly.DatumPlaneByPrincipalPlane(offset=206.98,
        principalPlane=XZPLANE)
    mdb.models['Model-1'].rootAssembly.PartitionCellByDatumPlane(cells=
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1'].cells.getSequenceFromMask(
        ('[#1 ]', ), ), datumPlane=mdb.models['Model-1'].rootAssembly.datums[145])
    mdb.models['Model-1'].rootAssembly.PartitionCellByDatumPlane(cells=
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1'].cells.getSequenceFromMask(
        ('[#1 ]', ), ), datumPlane=mdb.models['Model-1'].rootAssembly.datums[146])
    mdb.models['Model-1'].ConstrainedSketch(gridSpacing=27.0, name='__profile__',
        sheetSize=1080.28, transform=
        mdb.models['Model-1'].rootAssembly.MakeSketchTransform(
        sketchPlane=mdb.models['Model-1'].rootAssembly.instances['Chord-1'].faces[11],
        sketchPlaneSide=SIDE1,
        sketchUpEdge=mdb.models['Model-1'].rootAssembly.instances['Chord-1'].edges[36],
        sketchOrientation=RIGHT, origin=(195.58, 177.8, 262.5)))
    mdb.models['Model-1'].rootAssembly.projectReferencesOntoSketch(filter=
        COPLANAR_EDGES, sketch=mdb.models['Model-1'].sketches['__profile__'])
    mdb.models['Model-1'].sketches['__profile__'].offset(distance=5.08, objectList=
        (mdb.models['Model-1'].sketches['__profile__'].geometry[8],
        mdb.models['Model-1'].sketches['__profile__'].geometry[12],
        mdb.models['Model-1'].sketches['__profile__'].geometry[16],
        mdb.models['Model-1'].sketches['__profile__'].geometry[32],
        mdb.models['Model-1'].sketches['__profile__'].geometry[36]), side=LEFT)
    mdb.models['Model-1'].sketches['__profile__'].offset(distance=12.0, objectList=
        (mdb.models['Model-1'].sketches['__profile__'].geometry[38],
        mdb.models['Model-1'].sketches['__profile__'].geometry[39],
        mdb.models['Model-1'].sketches['__profile__'].geometry[40],
        mdb.models['Model-1'].sketches['__profile__'].geometry[41],
        mdb.models['Model-1'].sketches['__profile__'].geometry[42]), side=LEFT)
    mdb.models['Model-1'].rootAssembly.PartitionFaceBySketch(faces=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].faces.getSequenceFromMask(
        ('[#800 ]', ), ), sketch=mdb.models['Model-1'].sketches['__profile__'],
        sketchUpEdge=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].edges[36])
    del mdb.models['Model-1'].sketches['__profile__']
    mdb.models['Model-1'].rootAssembly.PartitionCellByPlaneThreePoints(cells=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].cells.getSequenceFromMask(
        ('[#1 ]', ), ), point1=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].vertices[12],
        point2=mdb.models['Model-1'].rootAssembly.instances['Chord-1'].vertices[17]
        , point3=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].InterestingPoint(
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].edges[3], MIDDLE))
    mdb.models['Model-1'].rootAssembly.PartitionCellByPlaneThreePoints(cells=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].cells.getSequenceFromMask(
        ('[#2 ]', ), ), point1=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].vertices[15],
        point2=mdb.models['Model-1'].rootAssembly.instances['Chord-1'].vertices[18]
        , point3=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].InterestingPoint(
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].edges[31], MIDDLE))


    # ----------
    mdb.models['Model-1'].rootAssembly.DatumPlaneByPointNormal(normal=
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1'].edges[1],
        point=
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1'].vertices[2])
    mdb.models['Model-1'].rootAssembly.DatumPlaneByPointNormal(normal=
        mdb.models['Model-1'].rootAssembly.instances['SideWeld-1'].edges[1], point=
        mdb.models['Model-1'].rootAssembly.instances['SideWeld-1'].vertices[1])
    mdb.models['Model-1'].rootAssembly.DatumPlaneByPointNormal(normal=
        mdb.models['Model-1'].rootAssembly.instances['SideWeld-1'].edges[1], point=
        mdb.models['Model-1'].rootAssembly.instances['SideWeld-1'].vertices[2])
    mdb.models['Model-1'].rootAssembly.DatumPlaneByThreePoints(point1=
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1'].InterestingPoint(
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1'].edges[2], MIDDLE),
        point2=
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1'].InterestingPoint(
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1'].edges[1],
        MIDDLE), point3=
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1'].InterestingPoint(
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1'].edges[5],
        MIDDLE))
    mdb.models['Model-1'].rootAssembly.DatumPlaneByThreePoints(point1=
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1'].InterestingPoint(
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1'].edges[1],
        MIDDLE), point2=
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1'].InterestingPoint(
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1'].edges[21], MIDDLE)
        , point3=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].InterestingPoint(
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].edges[44], MIDDLE))
    mdb.models['Model-1'].rootAssembly.PartitionFaceByDatumPlane(datumPlane=
        mdb.models['Model-1'].rootAssembly.datums[152], faces=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].faces.getSequenceFromMask(
        ('[#800800 ]', ), ))
    mdb.models['Model-1'].rootAssembly.PartitionFaceByDatumPlane(datumPlane=
        mdb.models['Model-1'].rootAssembly.datums[153], faces=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].faces.getSequenceFromMask(
        ('[#5 ]', ), ))
    mdb.models['Model-1'].rootAssembly.PartitionFaceByDatumPlane(datumPlane=
        mdb.models['Model-1'].rootAssembly.datums[154], faces=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].faces.getSequenceFromMask(
        ('[#14 ]', ), ))
    mdb.models['Model-1'].rootAssembly.PartitionFaceByDatumPlane(datumPlane=
        mdb.models['Model-1'].rootAssembly.datums[155], faces=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].faces.getSequenceFromMask(
        ('[#c ]', ), ))
    mdb.models['Model-1'].rootAssembly.PartitionFaceByDatumPlane(datumPlane=
        mdb.models['Model-1'].rootAssembly.datums[156], faces=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].faces.getSequenceFromMask(
        ('[#140 ]', ), ))
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1'].edges.getSequenceFromMask(
        mask=('[#11108000 #1 #e120 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].edges.getSequenceFromMask(
        mask=('[#8290b75 ]', ), ), size=2.0)
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1'].edges.getSequenceFromMask(
        mask=('[#aaa8001e #4444000a #2 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['SideWeld-1'].edges.getSequenceFromMask(
        mask=('[#22 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].edges.getSequenceFromMask(
        mask=('[#254b48a ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1'].edges.getSequenceFromMask(
        mask=('[#22 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1'].edges.getSequenceFromMask(
        mask=('[#22 ]', ), ), size=4.0)
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-1-2'].edges.getSequenceFromMask(
        mask=('[#22 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].edges.getSequenceFromMask(
        mask=('[#0 #4:2 ]', ), ), size=4.0)
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].edges.getSequenceFromMask(
        mask=('[#0 #1000002 #40e00 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1'].edges.getSequenceFromMask(
        mask=('[#0 #22220000 ]', ), ), number=16)
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].edges.getSequenceFromMask(
        ('[#0 #c0000000 #500000 ]', ), ), size=4.0)
    mdb.models['Model-1'].rootAssembly.seedPartInstance(deviationFactor=0.1,
        minSizeFactor=0.1, regions=(
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1-1'], ),
        size=2.8)
    mdb.models['Model-1'].rootAssembly.seedPartInstance(deviationFactor=0.1,
        minSizeFactor=0.1, regions=(
        mdb.models['Model-1'].rootAssembly.instances['SideWeld-1-lin-2-1'], ),
        size=4.0)
    mdb.models['Model-1'].rootAssembly.seedPartInstance(deviationFactor=0.1,
        minSizeFactor=0.1, regions=(
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1-lin-2-1'],
        ), size=2.8)
    mdb.models['Model-1'].rootAssembly.seedPartInstance(deviationFactor=0.1,
        minSizeFactor=0.1, regions=(
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-1-2-lin-2-1'],
        ), size=2.9)
    mdb.models['Model-1'].rootAssembly.seedPartInstance(deviationFactor=0.1,
        minSizeFactor=0.1, regions=(
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-2-1'], ),
        size=2.9)
    mdb.models['Model-1'].rootAssembly.seedPartInstance(deviationFactor=0.1,
        minSizeFactor=0.1, regions=(
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1-lin-2-1'], ), size=
        13.0)
    mdb.models['Model-1'].rootAssembly.seedPartInstance(deviationFactor=0.1,
        minSizeFactor=0.1, regions=(
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1'], ),
        size=2.8)
    mdb.models['Model-1'].rootAssembly.seedPartInstance(deviationFactor=0.1,
        minSizeFactor=0.1, regions=(
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1'], ), size=2.8)
    mdb.models['Model-1'].rootAssembly.seedPartInstance(deviationFactor=0.1,
        minSizeFactor=0.1, regions=(
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1'], ), size=12.0)
    mdb.models['Model-1'].rootAssembly.seedPartInstance(deviationFactor=0.1,
        minSizeFactor=0.1, regions=(
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-1-2'], ),
        size=2.9)
    mdb.models['Model-1'].rootAssembly.seedPartInstance(deviationFactor=0.1,
        minSizeFactor=0.1, regions=(
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1'], ), size=
        2.9)
    mdb.models['Model-1'].rootAssembly.seedPartInstance(deviationFactor=0.1,
        minSizeFactor=0.1, regions=(
        mdb.models['Model-1'].rootAssembly.instances['SideWeld-1'], ), size=4.0)
    mdb.models['Model-1'].rootAssembly.seedPartInstance(deviationFactor=0.1,
        minSizeFactor=0.1, regions=(
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'], ), size=26.0)
    mdb.models['Model-1'].rootAssembly.generateMesh(regions=(
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'],
        mdb.models['Model-1'].rootAssembly.instances['SideWeld-1'],
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1'],
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-1-2'],
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1'],
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1'],
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1'],
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1-lin-2-1'],
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-2-1'],
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-1-2-lin-2-1'],
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1-lin-2-1'],
        mdb.models['Model-1'].rootAssembly.instances['SideWeld-1-lin-2-1'],
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1-1']))


    # ----------
    mdb.models['Model-1'].rootAssembly.Set(name='Set-1', nodes=
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1'].nodes.getSequenceFromMask(
        mask=('[#ff000000 #f #0:11 #fffff000 #ffffffff #3ffff ]', ), ))
    mdb.models['Model-1'].rootAssembly.DatumPointByMidPoint(point1=
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1'].vertices[12],
        point2=
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1'].vertices[24])
    mdb.models['Model-1'].rootAssembly.ReferencePoint(point=
        mdb.models['Model-1'].rootAssembly.datums[181])
    mdb.models['Model-1'].RigidBody(name='LoadingPlate', refPointRegion=Region(
        referencePoints=(mdb.models['Model-1'].rootAssembly.referencePoints[182],
        )), tieRegion=mdb.models['Model-1'].rootAssembly.sets['Set-1'])
    mdb.models['Model-1'].rootAssembly.Set(name='Set-18', referencePoints=(
        mdb.models['Model-1'].rootAssembly.referencePoints[182], ))
    mdb.models['Model-1'].ConcentratedForce(cf2=-36.15, createStepName='Step-1',
        distributionType=UNIFORM, field='', localCsys=None, name='Load-1', region=
        mdb.models['Model-1'].rootAssembly.sets['Set-18'])
    mdb.models['Model-1'].rootAssembly.Set(name='Set-3', nodes=
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1-lin-2-1'].nodes.getSequenceFromMask(
        mask=('[#3ffffff ]', ), ))
    mdb.models['Model-1'].DisplacementBC(amplitude=UNSET, createStepName='Initial',
        distributionType=UNIFORM, fieldName='', localCsys=None, name='BC-1',
        region=mdb.models['Model-1'].rootAssembly.sets['Set-3'], u1=UNSET, u2=UNSET
        , u3=SET, ur1=UNSET, ur2=UNSET, ur3=UNSET)
    mdb.models['Model-1'].boundaryConditions['BC-1'].setValues(u1=SET, u2=SET, ur1=
        SET, ur2=SET, ur3=SET)
    mdb.models['Model-1'].rootAssembly.Set(faces=
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1-lin-2-1'].faces.getSequenceFromMask(
        mask=('[#3 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-2-1'].faces.getSequenceFromMask(
        mask=('[#8 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].faces.getSequenceFromMask(
        mask=('[#886000 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-1-2-lin-2-1'].faces.getSequenceFromMask(
        mask=('[#10 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1'].faces.getSequenceFromMask(
        mask=('[#e009002 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-1-2'].faces.getSequenceFromMask(
        mask=('[#10 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1'].faces.getSequenceFromMask(
        mask=('[#8 ]', ), ), name='Set-20')
    mdb.models['Model-1'].DisplacementBC(amplitude=UNSET, createStepName='Initial',
        distributionType=UNIFORM, fieldName='', localCsys=None, name='BC-2',
        region=mdb.models['Model-1'].rootAssembly.sets['Set-20'], u1=UNSET, u2=
        UNSET, u3=SET, ur1=UNSET, ur2=UNSET, ur3=UNSET)
    mdb.models['Model-1'].constraints.delete(('brace-chord', 'chord-brace'))
    mdb.models['Model-1'].rootAssembly.Surface(name='m_Surf-8', side1Faces=
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1'].faces.getSequenceFromMask(
        ('[#d1550554 #3 ]', ), ))
    mdb.models['Model-1'].rootAssembly.Surface(name='s_Surf-8', side1Faces=
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1'].faces.getSequenceFromMask(
        mask=('[#1 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1'].faces.getSequenceFromMask(
        mask=('[#1 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['SideWeld-1'].faces.getSequenceFromMask(
        mask=('[#1 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-1-2'].faces.getSequenceFromMask(
        mask=('[#1 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1'].faces.getSequenceFromMask(
        mask=('[#1 ]', ), ))
    mdb.models['Model-1'].Tie(adjust=ON, master=
        mdb.models['Model-1'].rootAssembly.surfaces['m_Surf-8'], name='brace-weld',
        positionToleranceMethod=COMPUTED, slave=
        mdb.models['Model-1'].rootAssembly.surfaces['s_Surf-8'], thickness=ON,
        tieRotations=ON)
    mdb.models['Model-1'].rootAssembly.Surface(name='m_Surf-10', side1Faces=
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1'].faces.getSequenceFromMask(
        mask=('[#4 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1'].faces.getSequenceFromMask(
        mask=('[#4 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['SideWeld-1'].faces.getSequenceFromMask(
        mask=('[#4 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1'].faces.getSequenceFromMask(
        mask=('[#4 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-1-2'].faces.getSequenceFromMask(
        mask=('[#4 ]', ), ))
    mdb.models['Model-1'].rootAssembly.Surface(name='s_Surf-10', side1Faces=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].faces.getSequenceFromMask(
        ('[#6007ff #4 ]', ), ))
    mdb.models['Model-1'].Tie(adjust=ON, master=
        mdb.models['Model-1'].rootAssembly.surfaces['m_Surf-10'], name='weld-chord'
        , positionToleranceMethod=COMPUTED, slave=
        mdb.models['Model-1'].rootAssembly.surfaces['s_Surf-10'], thickness=ON,
        tieRotations=ON)
    mdb.models['Model-1'].rootAssembly.Surface(name='m_Surf-12', side1Faces=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].faces.getSequenceFromMask(
        ('[#4000000 ]', ), ))
    mdb.models['Model-1'].rootAssembly.Surface(name='s_Surf-12', side1Faces=
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-1-2-lin-2-1'].faces.getSequenceFromMask(
        mask=('[#4 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1-1'].faces.getSequenceFromMask(
        mask=('[#4 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['SideWeld-1-lin-2-1'].faces.getSequenceFromMask(
        mask=('[#4 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1-lin-2-1'].faces.getSequenceFromMask(
        mask=('[#4 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-2-1'].faces.getSequenceFromMask(
        mask=('[#4 ]', ), ))
    mdb.models['Model-1'].Tie(adjust=ON, master=
        mdb.models['Model-1'].rootAssembly.surfaces['m_Surf-12'], name='chord-weld'
        , positionToleranceMethod=COMPUTED, slave=
        mdb.models['Model-1'].rootAssembly.surfaces['s_Surf-12'], thickness=ON,
        tieRotations=ON)
    mdb.models['Model-1'].rootAssembly.Surface(name='m_Surf-14', side1Faces=
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-2-1'].faces.getSequenceFromMask(
        mask=('[#1 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1-lin-2-1'].faces.getSequenceFromMask(
        mask=('[#1 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['SideWeld-1-lin-2-1'].faces.getSequenceFromMask(
        mask=('[#1 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1-1'].faces.getSequenceFromMask(
        mask=('[#1 ]', ), )+\
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-1-2-lin-2-1'].faces.getSequenceFromMask(
        mask=('[#1 ]', ), ))
    mdb.models['Model-1'].rootAssembly.Surface(name='s_Surf-14', side1Faces=
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1-lin-2-1'].faces.getSequenceFromMask(
        ('[#f4 ]', ), ))
    mdb.models['Model-1'].Tie(adjust=ON, master=
        mdb.models['Model-1'].rootAssembly.surfaces['m_Surf-14'], name='weld-brace'
        , positionToleranceMethod=COMPUTED, slave=
        mdb.models['Model-1'].rootAssembly.surfaces['s_Surf-14'], thickness=ON,
        tieRotations=ON)
    mdb.Job(atTime=None, contactPrint=OFF, description='', echoPrint=OFF,
        explicitPrecision=SINGLE, getMemoryFromAnalysis=True, historyPrint=OFF,
        memory=90, memoryUnits=PERCENTAGE, model='Model-1', modelPrint=OFF,
        multiprocessingMode=DEFAULT, name='Job-1NoHoletieOnly178x89',
        nodalOutputPrecision=SINGLE, numCpus=1, numGPUs=0, queue=None,
        resultsFormat=ODB, scratch='', type=ANALYSIS, userSubroutine='', waitHours=
        0, waitMinutes=0)
    mdb.jobs['Job-1NoHoletieOnly178x89'].submit(consistencyChecking=OFF)
    mdb.jobs['Job-1NoHoletieOnly178x89']._Message(STARTED, {
        'phase': STANDARD_PHASE, 'clientHost': 'Sara', 'handle': 2560,
        'jobName': 'Job-1NoHoletieOnly178x89'})
    mdb.jobs['Job-1NoHoletieOnly178x89']._Message(STEP, {'phase': STANDARD_PHASE,
        'stepId': 1, 'jobName': 'Job-1NoHoletieOnly178x89'})
    mdb.jobs['Job-1NoHoletieOnly178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 0,
        'jobName': 'Job-1NoHoletieOnly178x89'})
    mdb.jobs['Job-1NoHoletieOnly178x89']._Message(STATUS, {'totalTime': 0.0,
        'attempts': 0, 'timeIncrement': 0.2, 'increment': 0, 'stepTime': 0.0,
        'step': 1, 'jobName': 'Job-1NoHoletieOnly178x89', 'severe': 0,
        'iterations': 0, 'phase': STANDARD_PHASE, 'equilibrium': 0})
    mdb.jobs['Job-1NoHoletieOnly178x89']._Message(MEMORY_ESTIMATE, {
        'phase': STANDARD_PHASE, 'jobName': 'Job-1NoHoletieOnly178x89',
        'memory': 120.0})
    mdb.jobs['Job-1NoHoletieOnly178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 1,
        'jobName': 'Job-1NoHoletieOnly178x89'})
    mdb.jobs['Job-1NoHoletieOnly178x89']._Message(STATUS, {'totalTime': 0.2,
        'attempts': 1, 'timeIncrement': 0.2, 'increment': 1, 'stepTime': 0.2,
        'step': 1, 'jobName': 'Job-1NoHoletieOnly178x89', 'severe': 0,
        'iterations': 3, 'phase': STANDARD_PHASE, 'equilibrium': 3})
    mdb.jobs['Job-1NoHoletieOnly178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 2,
        'jobName': 'Job-1NoHoletieOnly178x89'})
    mdb.jobs['Job-1NoHoletieOnly178x89']._Message(STATUS, {'totalTime': 0.4,
        'attempts': 1, 'timeIncrement': 0.2, 'increment': 2, 'stepTime': 0.4,
        'step': 1, 'jobName': 'Job-1NoHoletieOnly178x89', 'severe': 0,
        'iterations': 2, 'phase': STANDARD_PHASE, 'equilibrium': 2})
    mdb.jobs['Job-1NoHoletieOnly178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 3,
        'jobName': 'Job-1NoHoletieOnly178x89'})
    mdb.jobs['Job-1NoHoletieOnly178x89']._Message(STATUS, {'totalTime': 0.7,
        'attempts': 1, 'timeIncrement': 0.3, 'increment': 3, 'stepTime': 0.7,
        'step': 1, 'jobName': 'Job-1NoHoletieOnly178x89', 'severe': 0,
        'iterations': 2, 'phase': STANDARD_PHASE, 'equilibrium': 2})
    mdb.jobs['Job-1NoHoletieOnly178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 4,
        'jobName': 'Job-1NoHoletieOnly178x89'})
    mdb.jobs['Job-1NoHoletieOnly178x89']._Message(STATUS, {'totalTime': 1.0,
        'attempts': 1, 'timeIncrement': 0.3, 'increment': 4, 'stepTime': 1.0,
        'step': 1, 'jobName': 'Job-1NoHoletieOnly178x89', 'severe': 0,
        'iterations': 3, 'phase': STANDARD_PHASE, 'equilibrium': 3})
    mdb.jobs['Job-1NoHoletieOnly178x89']._Message(END_STEP, {
        'phase': STANDARD_PHASE, 'stepId': 1,
        'jobName': 'Job-1NoHoletieOnly178x89'})
    mdb.jobs['Job-1NoHoletieOnly178x89']._Message(COMPLETED, {
        'phase': STANDARD_PHASE, 'message': 'Analysis phase complete',
        'jobName': 'Job-1NoHoletieOnly178x89'})
    mdb.jobs['Job-1NoHoletieOnly178x89']._Message(JOB_COMPLETED, {
        'time': 'Sun Aug 26 18:25:17 2018', 'jobName': 'Job-1NoHoletieOnly178x89'})
    mdb.models['Model-1'].rootAssembly.Surface(name='m_Surf-16', side1Faces=
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1'].faces.getSequenceFromMask(
        ('[#d0000000 #3 ]', ), ))
    mdb.models['Model-1'].constraints['brace-weld'].setValues(master=
        mdb.models['Model-1'].rootAssembly.surfaces['m_Surf-16'])
    mdb.models['Model-1'].rootAssembly.Surface(name='s_Surf-17', side1Faces=
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'].faces.getSequenceFromMask(
        ('[#1a6 #4 ]', ), ))
    mdb.models['Model-1'].constraints['weld-chord'].setValues(slave=
        mdb.models['Model-1'].rootAssembly.surfaces['s_Surf-17'])
    mdb.Job(atTime=None, contactPrint=OFF, description='', echoPrint=OFF,
        explicitPrecision=SINGLE, getMemoryFromAnalysis=True, historyPrint=OFF,
        memory=90, memoryUnits=PERCENTAGE, model='Model-1', modelPrint=OFF,
        multiprocessingMode=DEFAULT, name='Job-2NoHoleTieOnly178x89',
        nodalOutputPrecision=SINGLE, numCpus=1, numGPUs=0, queue=None,
        resultsFormat=ODB, scratch='', type=ANALYSIS, userSubroutine='', waitHours=
        0, waitMinutes=0)
    mdb.jobs['Job-2NoHoleTieOnly178x89'].submit(consistencyChecking=OFF)


    # ----------
    mdb.Job(atTime=None, contactPrint=OFF, description='', echoPrint=OFF,
        explicitPrecision=SINGLE, getMemoryFromAnalysis=True, historyPrint=OFF,
        memory=90, memoryUnits=PERCENTAGE, model='Model-1', modelPrint=OFF,
        multiprocessingMode=DEFAULT, name='Job-3NoHoleTieOnly178x89',
        nodalOutputPrecision=SINGLE, numCpus=1, numGPUs=0, queue=None,
        resultsFormat=ODB, scratch='', type=ANALYSIS, userSubroutine='', waitHours=
        0, waitMinutes=0)
    mdb.jobs['Job-3NoHoleTieOnly178x89'].submit(consistencyChecking=OFF)
    mdb.jobs['Job-3NoHoleTieOnly178x89']._Message(ERROR, {
        'message': 'XML parsing failure for job Job-3NoHoleTieOnly178x89.  Shutting down socket and terminating all further messages.  Please check the .log, .dat, .sta, or .msg files for information about the status of the job.',
        'jobName': 'Job-3NoHoleTieOnly178x89'})
    mdb.jobs['Job-3NoHoleTieOnly178x89']._Message(JOB_ABORTED, {})
    mdb.models['Model-1'].steps['Step-1'].setValues(initialInc=0.1, maxInc=0.1)
    mdb.models['Model-1'].StaticStep(name='Step-2', previous='Step-1')
    del mdb.models['Model-1'].steps['Step-2']
    mdb.models['Model-1'].steps['Step-1'].setValues(maxNumInc=10000)
    mdb.Job(atTime=None, contactPrint=OFF, description='', echoPrint=OFF,
        explicitPrecision=SINGLE, getMemoryFromAnalysis=True, historyPrint=OFF,
        memory=90, memoryUnits=PERCENTAGE, model='Model-1', modelPrint=OFF,
        multiprocessingMode=DEFAULT, name='Job-4NoHoleTieOnly178x89',
        nodalOutputPrecision=SINGLE, numCpus=1, numGPUs=0, queue=None,
        resultsFormat=ODB, scratch='', type=ANALYSIS, userSubroutine='', waitHours=
        0, waitMinutes=0)
    mdb.jobs['Job-4NoHoleTieOnly178x89'].submit(consistencyChecking=OFF)
    mdb.jobs['Job-4NoHoleTieOnly178x89']._Message(JOB_COMPLETED, {
        'time': 'Sun Aug 26 18:58:16 2018', 'jobName': 'Job-4NoHoleTieOnly178x89'})
    mdb.models['Model-1'].steps['Step-1'].setValues(maxInc=1.0)
    mdb.Job(atTime=None, contactPrint=OFF, description='', echoPrint=OFF,
        explicitPrecision=SINGLE, getMemoryFromAnalysis=True, historyPrint=OFF,
        memory=90, memoryUnits=PERCENTAGE, model='Model-1', modelPrint=OFF,
        multiprocessingMode=DEFAULT, name='Job-5NoHOleTieOnly178x89',
        nodalOutputPrecision=SINGLE, numCpus=1, numGPUs=0, queue=None,
        resultsFormat=ODB, scratch='', type=ANALYSIS, userSubroutine='', waitHours=
        0, waitMinutes=0)
    mdb.jobs['Job-5NoHOleTieOnly178x89'].submit(consistencyChecking=OFF)
    mdb.jobs['Job-5NoHOleTieOnly178x89']._Message(STARTED, {
        'phase': STANDARD_PHASE, 'clientHost': 'Sara', 'handle': 6504,
        'jobName': 'Job-5NoHOleTieOnly178x89'})
    mdb.jobs['Job-5NoHOleTieOnly178x89']._Message(STEP, {'phase': STANDARD_PHASE,
        'stepId': 1, 'jobName': 'Job-5NoHOleTieOnly178x89'})
    mdb.jobs['Job-5NoHOleTieOnly178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 0,
        'jobName': 'Job-5NoHOleTieOnly178x89'})
    mdb.jobs['Job-5NoHOleTieOnly178x89']._Message(STATUS, {'totalTime': 0.0,
        'attempts': 0, 'timeIncrement': 0.1, 'increment': 0, 'stepTime': 0.0,
        'step': 1, 'jobName': 'Job-5NoHOleTieOnly178x89', 'severe': 0,
        'iterations': 0, 'phase': STANDARD_PHASE, 'equilibrium': 0})
    mdb.jobs['Job-5NoHOleTieOnly178x89']._Message(MEMORY_ESTIMATE, {
        'phase': STANDARD_PHASE, 'jobName': 'Job-5NoHOleTieOnly178x89',
        'memory': 119.0})
    mdb.jobs['Job-5NoHOleTieOnly178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 1,
        'jobName': 'Job-5NoHOleTieOnly178x89'})
    mdb.jobs['Job-5NoHOleTieOnly178x89']._Message(STATUS, {'totalTime': 0.1,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 1, 'stepTime': 0.1,
        'step': 1, 'jobName': 'Job-5NoHOleTieOnly178x89', 'severe': 0,
        'iterations': 2, 'phase': STANDARD_PHASE, 'equilibrium': 2})
    mdb.jobs['Job-5NoHOleTieOnly178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 2,
        'jobName': 'Job-5NoHOleTieOnly178x89'})
    mdb.jobs['Job-5NoHOleTieOnly178x89']._Message(STATUS, {'totalTime': 0.2,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 2, 'stepTime': 0.2,
        'step': 1, 'jobName': 'Job-5NoHOleTieOnly178x89', 'severe': 0,
        'iterations': 2, 'phase': STANDARD_PHASE, 'equilibrium': 2})
    mdb.jobs['Job-5NoHOleTieOnly178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 3,
        'jobName': 'Job-5NoHOleTieOnly178x89'})
    mdb.jobs['Job-5NoHOleTieOnly178x89']._Message(STATUS, {'totalTime': 0.35,
        'attempts': 1, 'timeIncrement': 0.15, 'increment': 3, 'stepTime': 0.35,
        'step': 1, 'jobName': 'Job-5NoHOleTieOnly178x89', 'severe': 0,
        'iterations': 2, 'phase': STANDARD_PHASE, 'equilibrium': 2})
    mdb.jobs['Job-5NoHOleTieOnly178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 4,
        'jobName': 'Job-5NoHOleTieOnly178x89'})
    mdb.jobs['Job-5NoHOleTieOnly178x89']._Message(STATUS, {'totalTime': 0.575,
        'attempts': 1, 'timeIncrement': 0.225, 'increment': 4, 'stepTime': 0.575,
        'step': 1, 'jobName': 'Job-5NoHOleTieOnly178x89', 'severe': 0,
        'iterations': 2, 'phase': STANDARD_PHASE, 'equilibrium': 2})
    mdb.jobs['Job-5NoHOleTieOnly178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 5,
        'jobName': 'Job-5NoHOleTieOnly178x89'})
    mdb.jobs['Job-5NoHOleTieOnly178x89']._Message(STATUS, {'totalTime': 0.9125,
        'attempts': 1, 'timeIncrement': 0.3375, 'increment': 5, 'stepTime': 0.9125,
        'step': 1, 'jobName': 'Job-5NoHOleTieOnly178x89', 'severe': 0,
        'iterations': 3, 'phase': STANDARD_PHASE, 'equilibrium': 3})
    mdb.jobs['Job-5NoHOleTieOnly178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 6,
        'jobName': 'Job-5NoHOleTieOnly178x89'})
    mdb.jobs['Job-5NoHOleTieOnly178x89']._Message(STATUS, {'totalTime': 1.0,
        'attempts': 1, 'timeIncrement': 0.0874999999999999, 'increment': 6,
        'stepTime': 1.0, 'step': 1, 'jobName': 'Job-5NoHOleTieOnly178x89',
        'severe': 0, 'iterations': 2, 'phase': STANDARD_PHASE, 'equilibrium': 2})
    mdb.jobs['Job-5NoHOleTieOnly178x89']._Message(END_STEP, {
        'phase': STANDARD_PHASE, 'stepId': 1,
        'jobName': 'Job-5NoHOleTieOnly178x89'})
    mdb.jobs['Job-5NoHOleTieOnly178x89']._Message(COMPLETED, {
        'phase': STANDARD_PHASE, 'message': 'Analysis phase complete',
        'jobName': 'Job-5NoHOleTieOnly178x89'})
    mdb.jobs['Job-5NoHOleTieOnly178x89']._Message(JOB_COMPLETED, {
        'time': 'Sun Aug 26 19:07:05 2018', 'jobName': 'Job-5NoHOleTieOnly178x89'})


    # ----------
    mdb.models['Model-1'].rootAssembly._previewMergeMeshes(instances=(
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1'],
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1'],
        mdb.models['Model-1'].rootAssembly.instances['SideWeld-1'],
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1'],
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-1-2']),
        keepOnlyOrphanElems=True, mergeBoundaryOnly=False, nodeMergingTolerance=
        1e-06, removeDuplicateElements=False)
    mdb.models['Model-1'].rootAssembly.InstanceFromBooleanMerge(domain=BOTH,
        instances=(mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1'],
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1'],
        mdb.models['Model-1'].rootAssembly.instances['SideWeld-1'],
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1'],
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-1-2']),
        keepIntersections=ON, mergeNodes=ALL, name='Part-1', nodeMergingTolerance=
        1e-06, originalInstances=SUPPRESS, removeDuplicateElements=False)
    mdb.models['Model-1'].rootAssembly._previewMergeMeshes(instances=(
        mdb.models['Model-1'].rootAssembly.instances['Chord-1'],
        mdb.models['Model-1'].rootAssembly.instances['Part-1-1']),
        keepOnlyOrphanElems=True, mergeBoundaryOnly=False, nodeMergingTolerance=
        1e-06, removeDuplicateElements=False)
    mdb.models['Model-1'].rootAssembly.InstanceFromBooleanMerge(domain=BOTH,
        instances=(mdb.models['Model-1'].rootAssembly.instances['Chord-1'],
        mdb.models['Model-1'].rootAssembly.instances['Part-1-1']),
        keepIntersections=ON, mergeNodes=ALL, name='Part-2', nodeMergingTolerance=
        1e-06, originalInstances=SUPPRESS, removeDuplicateElements=False)
    mdb.models['Model-1'].rootAssembly._previewMergeMeshes(instances=(
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-2-1'],
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1-lin-2-1'],
        mdb.models['Model-1'].rootAssembly.instances['SideWeld-1-lin-2-1'],
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1-1'],
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-1-2-lin-2-1'])
        , keepOnlyOrphanElems=True, mergeBoundaryOnly=False, nodeMergingTolerance=
        1e-06, removeDuplicateElements=False)
    mdb.models['Model-1'].rootAssembly.InstanceFromBooleanMerge(domain=BOTH,
        instances=(
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-2-1'],
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1-lin-2-1'],
        mdb.models['Model-1'].rootAssembly.instances['SideWeld-1-lin-2-1'],
        mdb.models['Model-1'].rootAssembly.instances['CornerWeld-1-lin-2-1-1'],
        mdb.models['Model-1'].rootAssembly.instances['HalfSideWeld-1-lin-1-2-lin-2-1'])
        , keepIntersections=ON, mergeNodes=ALL, name='Part-3',
        nodeMergingTolerance=1e-06, originalInstances=SUPPRESS,
        removeDuplicateElements=False)
    mdb.models['Model-1'].rootAssembly._previewMergeMeshes(instances=(
        mdb.models['Model-1'].rootAssembly.instances['Part-2-1'],
        mdb.models['Model-1'].rootAssembly.instances['Part-3-1']),
        keepOnlyOrphanElems=True, mergeBoundaryOnly=False, nodeMergingTolerance=
        1e-06, removeDuplicateElements=False)
    mdb.models['Model-1'].rootAssembly.InstanceFromBooleanMerge(domain=BOTH,
        instances=(mdb.models['Model-1'].rootAssembly.instances['Part-2-1'],
        mdb.models['Model-1'].rootAssembly.instances['Part-3-1']),
        keepIntersections=ON, mergeNodes=ALL, name='Part-4', nodeMergingTolerance=
        1e-06, originalInstances=SUPPRESS, removeDuplicateElements=False)
    mdb.models['Model-1'].rootAssembly._previewMergeMeshes(instances=(
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1'],
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1-lin-2-1'],
        mdb.models['Model-1'].rootAssembly.instances['Part-4-1']),
        keepOnlyOrphanElems=True, mergeBoundaryOnly=False, nodeMergingTolerance=
        1e-06, removeDuplicateElements=False)
    mdb.models['Model-1'].rootAssembly.InstanceFromBooleanMerge(domain=BOTH,
        instances=(mdb.models['Model-1'].rootAssembly.instances['Brace2-1'],
        mdb.models['Model-1'].rootAssembly.instances['Brace2-1-lin-2-1'],
        mdb.models['Model-1'].rootAssembly.instances['Part-4-1']),
        keepIntersections=ON, mergeNodes=ALL, name='Part-5', nodeMergingTolerance=
        1e-06, originalInstances=SUPPRESS, removeDuplicateElements=False)
    mdb.models['Model-1'].rootAssembly.makeIndependent(instances=(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'], ))
    mdb.models['Model-1'].rootAssembly.PartitionCellByPlanePointNormal(cells=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#10 ]', ), ), normal=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[102], point=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].vertices[67])
    mdb.models['Model-1'].rootAssembly.PartitionCellByPlanePointNormal(cells=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#20 ]', ), ), normal=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[110], point=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].vertices[73])
    mdb.models['Model-1'].ConstrainedSketch(gridSpacing=27.0, name='__profile__',
        sheetSize=1080.28, transform=
        mdb.models['Model-1'].rootAssembly.MakeSketchTransform(
        sketchPlane=mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].faces[40],
        sketchPlaneSide=SIDE1,
        sketchUpEdge=mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[38],
        sketchOrientation=RIGHT, origin=(195.58, 177.8, 245.097012)))
    mdb.models['Model-1'].rootAssembly.projectReferencesOntoSketch(filter=
        COPLANAR_EDGES, sketch=mdb.models['Model-1'].sketches['__profile__'])
    mdb.models['Model-1'].sketches['__profile__'].offset(distance=5.08, objectList=
        (mdb.models['Model-1'].sketches['__profile__'].geometry[11],
        mdb.models['Model-1'].sketches['__profile__'].geometry[15],
        mdb.models['Model-1'].sketches['__profile__'].geometry[16],
        mdb.models['Model-1'].sketches['__profile__'].geometry[17],
        mdb.models['Model-1'].sketches['__profile__'].geometry[18]), side=RIGHT)
    mdb.models['Model-1'].sketches['__profile__'].offset(distance=12.0, objectList=
        (mdb.models['Model-1'].sketches['__profile__'].geometry[37],
        mdb.models['Model-1'].sketches['__profile__'].geometry[38],
        mdb.models['Model-1'].sketches['__profile__'].geometry[39],
        mdb.models['Model-1'].sketches['__profile__'].geometry[40],
        mdb.models['Model-1'].sketches['__profile__'].geometry[41]), side=RIGHT)
    mdb.models['Model-1'].rootAssembly.PartitionFaceBySketch(faces=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].faces.getSequenceFromMask(
        ('[#0 #100 ]', ), ), sketch=mdb.models['Model-1'].sketches['__profile__'],
        sketchUpEdge=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[38])
    del mdb.models['Model-1'].sketches['__profile__']
    mdb.models['Model-1'].ConstrainedSketch(gridSpacing=27.0, name='__profile__',
        sheetSize=1080.28, transform=
        mdb.models['Model-1'].rootAssembly.MakeSketchTransform(
        sketchPlane=mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].faces[1],
        sketchPlaneSide=SIDE1,
        sketchUpEdge=mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[55],
        sketchOrientation=RIGHT, origin=(195.58, 177.8, 488.447694)))
    mdb.models['Model-1'].rootAssembly.projectReferencesOntoSketch(filter=
        COPLANAR_EDGES, sketch=mdb.models['Model-1'].sketches['__profile__'])
    mdb.models['Model-1'].sketches['__profile__'].Line(point1=(-28.57, -7.982306),
        point2=(-50.0123552028482, 22.1219628560092))
    mdb.models['Model-1'].sketches['__profile__'].CoincidentConstraint(
        addUndoState=False, entity1=
        mdb.models['Model-1'].sketches['__profile__'].vertices[34], entity2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[29])
    mdb.models['Model-1'].sketches['__profile__'].EqualDistanceConstraint(
        addUndoState=False, entity1=
        mdb.models['Model-1'].sketches['__profile__'].vertices[26], entity2=
        mdb.models['Model-1'].sketches['__profile__'].vertices[1], midpoint=
        mdb.models['Model-1'].sketches['__profile__'].vertices[34])
    mdb.models['Model-1'].sketches['__profile__'].Line(point1=(28.57, -7.982306),
        point2=(50.0123552028152, 22.1219628560328))
    mdb.models['Model-1'].sketches['__profile__'].CoincidentConstraint(
        addUndoState=False, entity1=
        mdb.models['Model-1'].sketches['__profile__'].vertices[35], entity2=
        mdb.models['Model-1'].sketches['__profile__'].geometry[27])
    mdb.models['Model-1'].sketches['__profile__'].EqualDistanceConstraint(
        addUndoState=False, entity1=
        mdb.models['Model-1'].sketches['__profile__'].vertices[22], entity2=
        mdb.models['Model-1'].sketches['__profile__'].vertices[25], midpoint=
        mdb.models['Model-1'].sketches['__profile__'].vertices[35])
    mdb.models['Model-1'].rootAssembly.PartitionFaceBySketch(faces=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].faces.getSequenceFromMask(
        ('[#2 #400 ]', ), ), sketch=mdb.models['Model-1'].sketches['__profile__'],
        sketchUpEdge=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[55])
    del mdb.models['Model-1'].sketches['__profile__']
    del mdb.models['Model-1'].rootAssembly.features['Partition face-8']
    mdb.models['Model-1'].rootAssembly.DatumPlaneByThreePoints(point1=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].InterestingPoint(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[15], MIDDLE)
        , point2=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].InterestingPoint(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[7], MIDDLE),
        point3=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].InterestingPoint(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[183],
        MIDDLE))
    mdb.models['Model-1'].rootAssembly.DatumPlaneByThreePoints(point1=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].InterestingPoint(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[9], MIDDLE),
        point2=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].InterestingPoint(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[4], MIDDLE),
        point3=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].InterestingPoint(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[212],
        MIDDLE))
    mdb.models['Model-1'].rootAssembly.PartitionFaceByDatumPlane(datumPlane=
        mdb.models['Model-1'].rootAssembly.datums[211], faces=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].faces.getSequenceFromMask(
        ('[#2 #400 ]', ), ))
    mdb.models['Model-1'].rootAssembly.DatumPlaneByThreePoints(point1=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].InterestingPoint(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[217],
        MIDDLE), point2=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].InterestingPoint(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[13], MIDDLE)
        , point3=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].InterestingPoint(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[9], MIDDLE))
    mdb.models['Model-1'].rootAssembly.PartitionFaceByDatumPlane(datumPlane=
        mdb.models['Model-1'].rootAssembly.datums[214], faces=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].faces.getSequenceFromMask(
        ('[#2 #1000 ]', ), ))
    mdb.models['Model-1'].rootAssembly.seedPartInstance(deviationFactor=0.1,
        minSizeFactor=0.1, regions=(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'], ), size=26.0)
    mdb.models['Model-1'].rootAssembly.generateMesh(regions=(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'], ))


    # ----------
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'], ))
    mdb.models['Model-1'].rootAssembly.DatumPlaneByPrincipalPlane(offset=426.55,
        principalPlane=XYPLANE)
    mdb.models['Model-1'].rootAssembly.PartitionCellByDatumPlane(cells=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#87 ]', ), ), datumPlane=mdb.models['Model-1'].rootAssembly.datums[217])
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0:2 #400620 #0:3 #11000100 #11 #380 ]', ), ), minSizeFactor=0.1, size=
        2.0)
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0:2 #4040000 ]', ), ), minSizeFactor=0.1, size=2.0)
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0:6 #400 ]', ), ), minSizeFactor=0.1, size=4.0)
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#200000 #4000 #22125080 #0 #40000000 #2020 #8005480',
        ' #80000a0a #10 ]'), ), minSizeFactor=0.1, size=4.0)
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0:6 #400000 #800000 ]', ), ), number=3)
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0:5 #202 #a0002800 #100000a0 #4 ]', ), ), number=8)
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0 #2000 #88840 ]', ), ), number=4)
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0 #8000 #1210100 ]', ), ), number=4)
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0:7 #49400000 ]', ), ), number=14)
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#80 ]', ), ), number=8)
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#20000 ]', ), ), number=8)
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#21000000 #400 ]', ), ), number=14)


    # ----------
    mdb.models['Model-1'].rootAssembly.DatumPlaneByPointNormal(normal=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[20], point=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].vertices[35])
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0 #4000200 ]', ), ), number=3)
    mdb.models['Model-1'].rootAssembly.generateMesh(regions=(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'], ))
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#66 ]', ), ))
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#10000000 #0:2 #28000 #0:2 #4 ]', ), ), number=8)
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#18 ]', ), ))
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0:3 #40000 ]', ), ), number=3)
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0:2 #8000000 ]', ), ), number=3)
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0 #10 #1 ]', ), ), number=8)
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#801 ]', ), ))
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#2 ]', ), ), number=10)
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0:2 #800000 ]', ), ), number=10)
    mdb.models['Model-1'].rootAssembly.generateMesh(regions=(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'], ))
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#801 ]', ), ))
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#2 #0 #800000 ]', ), ), size=4.0)
    mdb.models['Model-1'].rootAssembly.generateMesh(regions=(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'], ))
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#8 ]', ), ))
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0:3 #100 ]', ), ), minSizeFactor=0.1, size=4.0)
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#10 ]', ), ))
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#1000 ]', ), ), minSizeFactor=0.1, size=4.0)
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0 #400000 ]', ), ), minSizeFactor=0.1, size=4.0)
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#40000 ]', ), ))
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0:4 #200 ]', ), ), number=8)
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#80 ]', ), ))
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0:8 #2000000 ]', ), ), number=8)
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0:9 #4 ]', ), ), number=8)
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#100000 ]', ), ))
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0:3 #80000000 ]', ), ), number=8)
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#80000 ]', ), ))
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0:4 #20 ]', ), ), minSizeFactor=0.1, size=4.0)
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0:8 #20000000 #10 ]', ), ), minSizeFactor=0.1, size=4.0)
    mdb.models['Model-1'].rootAssembly.generateMesh(regions=(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'], ))


    # ----------
    del mdb.models['Model-1'].loads['Load-1']
    del mdb.models['Model-1'].boundaryConditions['BC-2']
    del mdb.models['Model-1'].boundaryConditions['BC-1']
    mdb.models['Model-1'].rootAssembly.Surface(name='Surf-18', side1Faces=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].faces.getSequenceFromMask(
        ('[#0:4 #100 ]', ), ))
    mdb.models['Model-1'].Pressure(amplitude=UNSET, createStepName='Step-1',
        distributionType=TOTAL_FORCE, field='', magnitude=-36.15, name='Load-1',
        region=mdb.models['Model-1'].rootAssembly.surfaces['Surf-18'])
    del mdb.models['Model-1'].loads['Load-1']
    mdb.models['Model-1'].rootAssembly.Set(name='load', nodes=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].nodes.getSequenceFromMask(
        mask=('[#0:4 #3ffc #0:52 #ffffffe0 #ffffffff #7fffff #0:205',
        ' #fffffffe #ffffffff #7fffff ]', ), ))
    mdb.models['Model-1'].rootAssembly.Set(name='bc', nodes=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].nodes.getSequenceFromMask(
        mask=('[#0:2 #c0000000 #3ff #0:36 #fc000000 #fff80200 #fe00',
        ' #1010000 #f01fff80 #1ff #0:199 #ffffff00 #7ffffff ]', ), ))
    mdb.models['Model-1'].rootAssembly.Set(name='symm', nodes=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].nodes.getSequenceFromMask(
        mask=('[#380000 #38038e #5fbff180 #30f08458 #8408430c #0:12 #e0',
        ' #0:2 #38000103 #0:2 #b000000 #0:7 #400000 #f0000000',
        ' #ff003c00 #1f #0 #fffffc00 #ffff #0 #fffff800',
        ' #3ffffff #0 #fe000000 #fe01ff #0:2 #30000 #6000000',
        ' #ffc00 #1fc1f00 #0 #3 #0 #ffff0000 #3ff',
        ' #c0000000 #ff0007ff #7f #c000 #81800000 #1f #f0000000',
        ' #c000003c #7 #fe7e00c0 #ffffff #0:61 #800000 #0:2',
        ' #1000 #8 #0 #1000000 #0:70 #fffffff0 #ffffffff',
        ' #7ff #0:11 #ffffff80 #3fff #0:36 #7fe00 #0:7',
        ' #ff800000 #1 #0:12 #fffffe00 #7 #0:20 #ffffff80',
        ' #1 #1fe00000 #0:5 #7f80 #0:50 #fffff800 #ffffffff', ' #1f ]', ), ))
    mdb.models['Model-1'].rootAssembly.DatumPointByMidPoint(point1=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].vertices[126],
        point2=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].vertices[136])
    mdb.models['Model-1'].constraints.delete(('weld-chord', 'weld-brace',
        'chord-weld', 'brace-weld'))
    del mdb.models['Model-1'].constraints['LoadingPlate']
    mdb.models['Model-1'].rootAssembly.ReferencePoint(point=
        mdb.models['Model-1'].rootAssembly.datums[253])
    mdb.models['Model-1'].RigidBody(name='Constraint-1', refPointRegion=Region(
        referencePoints=(mdb.models['Model-1'].rootAssembly.referencePoints[254],
        )), tieRegion=mdb.models['Model-1'].rootAssembly.sets['load'])
    mdb.models['Model-1'].rootAssembly.Set(name='Set-53', referencePoints=(
        mdb.models['Model-1'].rootAssembly.referencePoints[254], ))
    mdb.models['Model-1'].ConcentratedForce(cf2=36.15, createStepName='Step-1',
        distributionType=UNIFORM, field='', localCsys=None, name='Load-1', region=
        mdb.models['Model-1'].rootAssembly.sets['Set-53'])
    mdb.models['Model-1'].loads['Load-1'].setValues(cf2=-36.15, distributionType=
        UNIFORM, field='')
    mdb.models['Model-1'].DisplacementBC(amplitude=UNSET, createStepName='Initial',
        distributionType=UNIFORM, fieldName='', localCsys=None, name='BC-1',
        region=mdb.models['Model-1'].rootAssembly.sets['bc'], u1=SET, u2=SET, u3=
        SET, ur1=SET, ur2=SET, ur3=SET)
    mdb.models['Model-1'].DisplacementBC(amplitude=UNSET, createStepName='Initial',
        distributionType=UNIFORM, fieldName='', localCsys=None, name='BC-2',
        region=mdb.models['Model-1'].rootAssembly.sets['symm'], u1=UNSET, u2=UNSET,
        u3=SET, ur1=SET, ur2=SET, ur3=UNSET)


    # ----------
    mdb.models['Model-1'].steps['Step-1'].setValues(maxInc=0.1)
    mdb.Job(atTime=None, contactPrint=OFF, description='', echoPrint=OFF,
        explicitPrecision=SINGLE, getMemoryFromAnalysis=True, historyPrint=OFF,
        memory=90, memoryUnits=PERCENTAGE, model='Model-1', modelPrint=OFF,
        multiprocessingMode=DEFAULT, name='Job-6noholemergedhalffinal178x89',
        nodalOutputPrecision=SINGLE, numCpus=1, numGPUs=0, queue=None,
        resultsFormat=ODB, scratch='', type=ANALYSIS, userSubroutine='', waitHours=
        0, waitMinutes=0)
    mdb.jobs['Job-6noholemergedhalffinal178x89'].submit(consistencyChecking=OFF)
    mdb.jobs['Job-6noholemergedhalffinal178x89']._Message(ERROR, {
        'message': 'XML parsing failure for job Job-6noholemergedhalffinal178x89.  Shutting down socket and terminating all further messages.  Please check the .log, .dat, .sta, or .msg files for information about the status of the job.',
        'jobName': 'Job-6noholemergedhalffinal178x89'})
    mdb.jobs['Job-6noholemergedhalffinal178x89']._Message(JOB_ABORTED, {})
    mdb.jobs['Job-6noholemergedhalffinal178x89'].submit(consistencyChecking=OFF)
    mdb.jobs['Job-6noholemergedhalffinal178x89']._Message(ERROR, {
        'message': 'Detected lock file Job-6noholemergedhalffinal178x89.lck. Please confirm that no other applications are attempting to write to the output database associated with this job before removing the lock file and resubmitting.',
        'jobName': 'Job-6noholemergedhalffinal178x89'})
    mdb.jobs['Job-6noholemergedhalffinal178x89']._Message(JOB_ABORTED, {
        'message': 'Detected lock file Job-6noholemergedhalffinal178x89.lck. Please confirm that no other applications are attempting to write to the output database associated with this job before removing the lock file and resubmitting.',
        'jobName': 'Job-6noholemergedhalffinal178x89'})
    mdb.Job(atTime=None, contactPrint=OFF, description='', echoPrint=OFF,
        explicitPrecision=SINGLE, getMemoryFromAnalysis=True, historyPrint=OFF,
        memory=90, memoryUnits=PERCENTAGE, model='Model-1', modelPrint=OFF,
        multiprocessingMode=DEFAULT, name='Job-7X178x89noholemergedfinal',
        nodalOutputPrecision=SINGLE, numCpus=1, numGPUs=0, queue=None,
        resultsFormat=ODB, scratch='', type=ANALYSIS, userSubroutine='', waitHours=
        0, waitMinutes=0)
    mdb.jobs['Job-7X178x89noholemergedfinal'].submit(consistencyChecking=OFF)


    # ----------
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#1f000 ]', ), ))
    mdb.models['Model-1'].rootAssembly.seedEdgeByNumber(constraint=FINER, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0:4 #10000000 #111 ]', ), ), number=3)
    mdb.models['Model-1'].rootAssembly.generateMesh(regions=(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'], ))


    # ----------
    mdb.models['Model-1'].steps['Step-1'].setValues(maxNumInc=100)
    mdb.Job(atTime=None, contactPrint=OFF, description='', echoPrint=OFF,
        explicitPrecision=SINGLE, getMemoryFromAnalysis=True, historyPrint=OFF,
        memory=90, memoryUnits=PERCENTAGE, model='Model-1', modelPrint=OFF,
        multiprocessingMode=DEFAULT, name='Job-10noholemergedfinalX178x89',
        nodalOutputPrecision=SINGLE, numCpus=1, numGPUs=0, queue=None,
        resultsFormat=ODB, scratch='', type=ANALYSIS, userSubroutine='', waitHours=
        0, waitMinutes=0)
    del mdb.models['Model-1'].constraints['Constraint-1']
    del mdb.models['Model-1'].loads['Load-1']
    mdb.models['Model-1'].boundaryConditions.delete(('BC-1', 'BC-2'))
    mdb.models['Model-1'].rootAssembly.Set(name='BoundaryC', nodes=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].nodes.getSequenceFromMask(
        mask=('[#0:3 #fff0000 #0:42 #fe03ffe #8 #ffc01fc0 #fc01007',
        ' #203f8 #0:249 #fffc0000 #ffffffff #1 ]', ), ))
    mdb.models['Model-1'].rootAssembly.Set(name='Loadingplate', nodes=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].nodes.getSequenceFromMask(
        mask=('[#0:4 #fff00000 #0:58 #ff000000 #ffffffff:2 #3ff #0:262',
        ' #fffff000 #ffffffff:2 #3 ]', ), ))
    mdb.models['Model-1'].rootAssembly.Set(name='Symmetry', nodes=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].nodes.getSequenceFromMask(
        mask=('[#380000 #a038038e #800031b0 #3a18fff1 #c30c3a0 #0:12 #f80',
        ' #0:2 #181c00 #380 #0:2 #b0 #f800 #c0180000',
        ' #40007 #ffc00000 #fffffc00 #7f #0:7 #200 #e0078000',
        ' #fff801 #0 #fffffc00 #3fff #ffc00000 #3ffffff #0',
        ' #ffff0 #0 #3fe000 #7fdfc00 #0:2 #7c00000 #1ff800f0',
        ' #f800007c #c00 #180000 #f0000000 #1ff #1ffffff8 #0',
        ' #3ffe0000 #3000000 #0 #6 #0:62 #c00000 #0:4',
        ' #60 #200 #0 #40000000 #0:51 #fffffc00 #ffffffff',
        ' #f #0:69 #ffc00000 #ffffffff #1fffffff #0:11 #ffffffe0',
        ' #fff #0:26 #7fe #0:7 #3ff0000 #0:7 #ffc000',
        ' #0:10 #ffc #0:6 #c0000000 #ffffff #0:26 #fffc0000', ' #fff ]', ), ))


    # ----------
    mdb.models['Model-1'].DisplacementBC(amplitude=UNSET, createStepName='Initial',
        distributionType=UNIFORM, fieldName='', localCsys=None, name='BC-1',
        region=mdb.models['Model-1'].rootAssembly.sets['Symmetry'], u1=UNSET, u2=
        UNSET, u3=SET, ur1=UNSET, ur2=UNSET, ur3=UNSET)
    mdb.models['Model-1'].DisplacementBC(amplitude=UNSET, createStepName='Initial',
        distributionType=UNIFORM, fieldName='', localCsys=None, name='BC-2',
        region=mdb.models['Model-1'].rootAssembly.sets['BoundaryC'], u1=SET, u2=SET
        , u3=SET, ur1=SET, ur2=SET, ur3=SET)
    mdb.models['Model-1'].rootAssembly.Set(name='Set-57', referencePoints=(
        mdb.models['Model-1'].rootAssembly.referencePoints[254], ))
    mdb.models['Model-1'].ConcentratedForce(cf2=-36.15, createStepName='Step-1',
        distributionType=UNIFORM, field='', localCsys=None, name='Load-1', region=
        mdb.models['Model-1'].rootAssembly.sets['Set-57'])
    mdb.models['Model-1'].RigidBody(name='Constraint-1', refPointRegion=Region(
        referencePoints=(mdb.models['Model-1'].rootAssembly.referencePoints[254],
        )), tieRegion=mdb.models['Model-1'].rootAssembly.sets['Loadingplate'])
    mdb.jobs['Job-10noholemergedfinalX178x89'].submit(consistencyChecking=OFF)


    # ----------
    mdb.Job(atTime=None, contactPrint=OFF, description='', echoPrint=OFF,
        explicitPrecision=SINGLE, getMemoryFromAnalysis=True, historyPrint=OFF,
        memory=90, memoryUnits=PERCENTAGE, model='Model-1', modelPrint=OFF,
        multiprocessingMode=DEFAULT, name='Job-11FinalNoHolemerged178x89',
        nodalOutputPrecision=SINGLE, numCpus=1, numGPUs=0, queue=None,
        resultsFormat=ODB, scratch='', type=ANALYSIS, userSubroutine='', waitHours=
        0, waitMinutes=0)
    mdb.jobs['Job-11FinalNoHolemerged178x89'].submit(consistencyChecking=OFF)
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(STARTED, {
        'phase': STANDARD_PHASE, 'clientHost': 'Sara', 'handle': 12224,
        'jobName': 'Job-11FinalNoHolemerged178x89'})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(STEP, {
        'phase': STANDARD_PHASE, 'stepId': 1,
        'jobName': 'Job-11FinalNoHolemerged178x89'})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 0,
        'jobName': 'Job-11FinalNoHolemerged178x89'})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(STATUS, {'totalTime': 0.0,
        'attempts': 0, 'timeIncrement': 0.1, 'increment': 0, 'stepTime': 0.0,
        'step': 1, 'jobName': 'Job-11FinalNoHolemerged178x89', 'severe': 0,
        'iterations': 0, 'phase': STANDARD_PHASE, 'equilibrium': 0})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(MEMORY_ESTIMATE, {
        'phase': STANDARD_PHASE, 'jobName': 'Job-11FinalNoHolemerged178x89',
        'memory': 275.0})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 1,
        'jobName': 'Job-11FinalNoHolemerged178x89'})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(STATUS, {'totalTime': 0.1,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 1, 'stepTime': 0.1,
        'step': 1, 'jobName': 'Job-11FinalNoHolemerged178x89', 'severe': 0,
        'iterations': 2, 'phase': STANDARD_PHASE, 'equilibrium': 2})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 2,
        'jobName': 'Job-11FinalNoHolemerged178x89'})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(STATUS, {'totalTime': 0.2,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 2, 'stepTime': 0.2,
        'step': 1, 'jobName': 'Job-11FinalNoHolemerged178x89', 'severe': 0,
        'iterations': 1, 'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 3,
        'jobName': 'Job-11FinalNoHolemerged178x89'})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(STATUS, {'totalTime': 0.3,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 3, 'stepTime': 0.3,
        'step': 1, 'jobName': 'Job-11FinalNoHolemerged178x89', 'severe': 0,
        'iterations': 1, 'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 4,
        'jobName': 'Job-11FinalNoHolemerged178x89'})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(STATUS, {'totalTime': 0.4,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 4, 'stepTime': 0.4,
        'step': 1, 'jobName': 'Job-11FinalNoHolemerged178x89', 'severe': 0,
        'iterations': 1, 'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 5,
        'jobName': 'Job-11FinalNoHolemerged178x89'})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(STATUS, {'totalTime': 0.5,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 5, 'stepTime': 0.5,
        'step': 1, 'jobName': 'Job-11FinalNoHolemerged178x89', 'severe': 0,
        'iterations': 1, 'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 6,
        'jobName': 'Job-11FinalNoHolemerged178x89'})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(STATUS, {'totalTime': 0.6,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 6, 'stepTime': 0.6,
        'step': 1, 'jobName': 'Job-11FinalNoHolemerged178x89', 'severe': 0,
        'iterations': 1, 'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 7,
        'jobName': 'Job-11FinalNoHolemerged178x89'})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(STATUS, {'totalTime': 0.7,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 7, 'stepTime': 0.7,
        'step': 1, 'jobName': 'Job-11FinalNoHolemerged178x89', 'severe': 0,
        'iterations': 1, 'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 8,
        'jobName': 'Job-11FinalNoHolemerged178x89'})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(STATUS, {'totalTime': 0.8,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 8, 'stepTime': 0.8,
        'step': 1, 'jobName': 'Job-11FinalNoHolemerged178x89', 'severe': 0,
        'iterations': 1, 'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 9,
        'jobName': 'Job-11FinalNoHolemerged178x89'})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(STATUS, {'totalTime': 0.9,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 9, 'stepTime': 0.9,
        'step': 1, 'jobName': 'Job-11FinalNoHolemerged178x89', 'severe': 0,
        'iterations': 1, 'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 10,
        'jobName': 'Job-11FinalNoHolemerged178x89'})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(STATUS, {'totalTime': 1.0,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 10, 'stepTime': 1.0,
        'step': 1, 'jobName': 'Job-11FinalNoHolemerged178x89', 'severe': 0,
        'iterations': 1, 'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(END_STEP, {
        'phase': STANDARD_PHASE, 'stepId': 1,
        'jobName': 'Job-11FinalNoHolemerged178x89'})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(COMPLETED, {
        'phase': STANDARD_PHASE, 'message': 'Analysis phase complete',
        'jobName': 'Job-11FinalNoHolemerged178x89'})
    mdb.jobs['Job-11FinalNoHolemerged178x89']._Message(JOB_COMPLETED, {
        'time': 'Wed Sep 05 20:41:36 2018',
        'jobName': 'Job-11FinalNoHolemerged178x89'})


    # ----------
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'], ))
    mdb.models['Model-1'].rootAssembly.PartitionCellByPlanePointNormal(cells=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#1 ]', ), ), normal=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[89], point=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].vertices[59])
    mdb.models['Model-1'].rootAssembly.PartitionCellByPlanePointNormal(cells=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#2 ]', ), ), normal=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[115], point=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].vertices[76])
    mdb.models['Model-1'].rootAssembly.PartitionCellByPlanePointNormal(cells=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#1 ]', ), ), normal=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[20], point=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].vertices[17])
    mdb.models['Model-1'].rootAssembly.generateMesh(regions=(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'], ))
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'], ))
    mdb.models['Model-1'].rootAssembly.DatumPlaneByPointNormal(normal=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[37], point=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].vertices[74])
    mdb.models['Model-1'].rootAssembly.DatumPlaneByPointNormal(normal=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[78], point=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].vertices[74])
    mdb.models['Model-1'].rootAssembly.DatumPlaneByPointNormal(normal=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[20], point=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].vertices[9])
    mdb.models['Model-1'].rootAssembly.DatumPlaneByPointNormal(normal=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges[16], point=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].vertices[9])
    mdb.models['Model-1'].rootAssembly.PartitionFaceByDatumPlane(datumPlane=
        mdb.models['Model-1'].rootAssembly.datums[269], faces=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].faces.getSequenceFromMask(
        ('[#0 #200 ]', ), ))
    mdb.models['Model-1'].rootAssembly.PartitionFaceByDatumPlane(datumPlane=
        mdb.models['Model-1'].rootAssembly.datums[269], faces=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].faces.getSequenceFromMask(
        ('[#10 ]', ), ))
    mdb.models['Model-1'].rootAssembly.PartitionFaceByDatumPlane(datumPlane=
        mdb.models['Model-1'].rootAssembly.datums[267], faces=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].faces.getSequenceFromMask(
        ('[#2 ]', ), ))
    mdb.models['Model-1'].rootAssembly.PartitionFaceByDatumPlane(datumPlane=
        mdb.models['Model-1'].rootAssembly.datums[268], faces=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].faces.getSequenceFromMask(
        ('[#2 ]', ), ))
    mdb.models['Model-1'].rootAssembly.generateMesh(regions=(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'], ))
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#14000 ]', ), ))
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#2800 #0:3 #4100000 ]', ), ), size=2.0)
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#43802 ]', ), ))
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#800002 #800000 #4400 #0:3 #10000000 #a000004 #202000', ' #10400 ]'), ),
        size=2.0)
    mdb.models['Model-1'].rootAssembly.generateMesh(regions=(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'], ))
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#8 ]', ), ))
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0:3 #80000000 ]', ), ), minSizeFactor=0.1, size=2.0)
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#10200 ]', ), ))
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0:3 #200 #22000000 ]', ), ), minSizeFactor=0.1, size=2.0)
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#2 ]', ), ))
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#10000000 ]', ), ), minSizeFactor=0.1, size=2.0)
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#100 ]', ), ))
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#0:2 #800 ]', ), ), minSizeFactor=0.1, size=2.0)
    mdb.models['Model-1'].rootAssembly.generateMesh(regions=(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'], ))
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#30a ]', ), ))
    mdb.models['Model-1'].rootAssembly.seedEdgeBySize(constraint=FINER,
        deviationFactor=0.1, edges=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].edges.getSequenceFromMask(
        ('[#8000420 #0:2 #100 ]', ), ), minSizeFactor=0.1, size=2.0)
    mdb.models['Model-1'].rootAssembly.generateMesh(regions=(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'], ))
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#42dc ]', ), ))
    mdb.models['Model-1'].rootAssembly.PartitionCellByDatumPlane(cells=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#200 ]', ), ), datumPlane=
        mdb.models['Model-1'].rootAssembly.datums[269])
    mdb.models['Model-1'].rootAssembly.deleteMesh(regions=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#244 ]', ), ))
    mdb.models['Model-1'].rootAssembly.PartitionCellByDatumPlane(cells=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].cells.getSequenceFromMask(
        ('[#200 ]', ), ), datumPlane=
        mdb.models['Model-1'].rootAssembly.datums[269])
    mdb.models['Model-1'].rootAssembly.generateMesh(regions=(
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'], ))


    # ----------
    mdb.Job(atTime=None, contactPrint=OFF, description='', echoPrint=OFF,
        explicitPrecision=SINGLE, getMemoryFromAnalysis=True, historyPrint=OFF,
        memory=90, memoryUnits=PERCENTAGE, model='Model-1', modelPrint=OFF,
        multiprocessingMode=DEFAULT, name='Job-12-178x89-NoHole-Journal',
        nodalOutputPrecision=SINGLE, numCpus=1, numGPUs=0, queue=None,
        resultsFormat=ODB, scratch='', type=ANALYSIS, userSubroutine='', waitHours=
        0, waitMinutes=0)
    del mdb.models['Model-1'].boundaryConditions['BC-1']
    del mdb.models['Model-1'].boundaryConditions['BC-2']
    mdb.models['Model-1'].rootAssembly.Set(faces=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].faces.getSequenceFromMask(
        ('[#0:6 #4000 ]', ), ), name='Set-66')
    mdb.models['Model-1'].DisplacementBC(amplitude=UNSET, createStepName='Initial',
        distributionType=UNIFORM, fieldName='', localCsys=None, name='BC-1',
        region=mdb.models['Model-1'].rootAssembly.sets['Set-66'], u1=SET, u2=SET,
        u3=SET, ur1=SET, ur2=SET, ur3=SET)
    mdb.models['Model-1'].rootAssembly.Set(faces=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].faces.getSequenceFromMask(
        ('[#0:2 #2180000 #20000000 #200000 #e009 #6 ]', ), ), name='Set-67')
    mdb.models['Model-1'].DisplacementBC(amplitude=UNSET, createStepName='Initial',
        distributionType=UNIFORM, fieldName='', localCsys=None, name='BC-2',
        region=mdb.models['Model-1'].rootAssembly.sets['Set-67'], u1=UNSET, u2=
        UNSET, u3=SET, ur1=UNSET, ur2=UNSET, ur3=UNSET)
    mdb.Job(atTime=None, contactPrint=OFF, description='', echoPrint=OFF,
        explicitPrecision=SINGLE, getMemoryFromAnalysis=True, historyPrint=OFF,
        memory=90, memoryUnits=PERCENTAGE, model='Model-1', modelPrint=OFF,
        multiprocessingMode=DEFAULT, name='Job-13-178x89-NoHole-Journal',
        nodalOutputPrecision=SINGLE, numCpus=1, numGPUs=0, queue=None,
        resultsFormat=ODB, scratch='', type=ANALYSIS, userSubroutine='', waitHours=
        0, waitMinutes=0)
    del mdb.models['Model-1'].constraints['Constraint-1']
    mdb.models['Model-1'].rootAssembly.Set(faces=
        mdb.models['Model-1'].rootAssembly.instances['Part-5-1'].faces.getSequenceFromMask(
        ('[#0:5 #8000000 ]', ), ), name='t_Set-67')
    mdb.models['Model-1'].RigidBody(name='Constraint-1', refPointRegion=Region(
        referencePoints=(mdb.models['Model-1'].rootAssembly.referencePoints[254],
        )), tieRegion=mdb.models['Model-1'].rootAssembly.sets['t_Set-67'])
    mdb.jobs['Job-13-178x89-NoHole-Journal'].submit(consistencyChecking=OFF)
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(STARTED, {
        'phase': BATCHPRE_PHASE, 'clientHost': 'Sara', 'handle': 0,
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(WARNING, {
        'phase': BATCHPRE_PHASE,
        'message': '1012 elements are distorted. Either the isoparametric angles are out of the suggested limits or the triangular or tetrahedral quality measure is bad. The elements have been identified in element set WarnElemDistorted.',
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(WARNING, {
        'phase': BATCHPRE_PHASE,
        'message': '2 nodes associated with rigid bodies have boundary conditions prescribed at nodes other than the reference node. These boundary conditions will be transferred to the associated rigid body reference node.The reference nodes and the dependent nodes have been identified in node set WarnNodeOverconBoundRB.',
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(WARNING, {
        'phase': BATCHPRE_PHASE,
        'message': 'Nodes belonging to 1 RIGID BODIES have boundary conditions prescribed at nodes other than the reference node. These boundary conditions indicate the rigid bodies cannot rotate about certain axes. Zero rotational boundary conditions have been added to these reference nodes.The reference nodes have been identified in node set WarnNodeOverconBoundRBRot.',
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(WARNING, {
        'phase': BATCHPRE_PHASE,
        'message': 'Boundary conditions are specified on inactive dof of 123 nodes. The nodes have been identified in node set WarnNodeBCInactiveDof.',
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(ODB_FILE, {
        'phase': BATCHPRE_PHASE,
        'file': 'D:\\Abaqus Work Directory\\Job-13-178x89-NoHole-Journal.odb',
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(COMPLETED, {
        'phase': BATCHPRE_PHASE, 'message': 'Analysis phase complete',
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(STARTED, {
        'phase': STANDARD_PHASE, 'clientHost': 'Sara', 'handle': 11620,
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(STEP, {
        'phase': STANDARD_PHASE, 'stepId': 1,
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 0,
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(STATUS, {'totalTime': 0.0,
        'attempts': 0, 'timeIncrement': 0.1, 'increment': 0, 'stepTime': 0.0,
        'step': 1, 'jobName': 'Job-13-178x89-NoHole-Journal', 'severe': 0,
        'iterations': 0, 'phase': STANDARD_PHASE, 'equilibrium': 0})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(MEMORY_ESTIMATE, {
        'phase': STANDARD_PHASE, 'jobName': 'Job-13-178x89-NoHole-Journal',
        'memory': 437.0})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 1,
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(STATUS, {'totalTime': 0.1,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 1, 'stepTime': 0.1,
        'step': 1, 'jobName': 'Job-13-178x89-NoHole-Journal', 'severe': 0,
        'iterations': 2, 'phase': STANDARD_PHASE, 'equilibrium': 2})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 2,
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(STATUS, {'totalTime': 0.2,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 2, 'stepTime': 0.2,
        'step': 1, 'jobName': 'Job-13-178x89-NoHole-Journal', 'severe': 0,
        'iterations': 1, 'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 3,
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(STATUS, {'totalTime': 0.3,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 3, 'stepTime': 0.3,
        'step': 1, 'jobName': 'Job-13-178x89-NoHole-Journal', 'severe': 0,
        'iterations': 1, 'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 4,
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(STATUS, {'totalTime': 0.4,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 4, 'stepTime': 0.4,
        'step': 1, 'jobName': 'Job-13-178x89-NoHole-Journal', 'severe': 0,
        'iterations': 1, 'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 5,
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(STATUS, {'totalTime': 0.5,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 5, 'stepTime': 0.5,
        'step': 1, 'jobName': 'Job-13-178x89-NoHole-Journal', 'severe': 0,
        'iterations': 1, 'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 6,
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(STATUS, {'totalTime': 0.6,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 6, 'stepTime': 0.6,
        'step': 1, 'jobName': 'Job-13-178x89-NoHole-Journal', 'severe': 0,
        'iterations': 1, 'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 7,
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(STATUS, {'totalTime': 0.7,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 7, 'stepTime': 0.7,
        'step': 1, 'jobName': 'Job-13-178x89-NoHole-Journal', 'severe': 0,
        'iterations': 1, 'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 8,
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(STATUS, {'totalTime': 0.8,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 8, 'stepTime': 0.8,
        'step': 1, 'jobName': 'Job-13-178x89-NoHole-Journal', 'severe': 0,
        'iterations': 1, 'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 9,
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(STATUS, {'totalTime': 0.9,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 9, 'stepTime': 0.9,
        'step': 1, 'jobName': 'Job-13-178x89-NoHole-Journal', 'severe': 0,
        'iterations': 1, 'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(ODB_FRAME, {
        'phase': STANDARD_PHASE, 'step': 0, 'frame': 10,
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(STATUS, {'totalTime': 1.0,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 10, 'stepTime': 1.0,
        'step': 1, 'jobName': 'Job-13-178x89-NoHole-Journal', 'severe': 0,
        'iterations': 1, 'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(END_STEP, {
        'phase': STANDARD_PHASE, 'stepId': 1,
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(COMPLETED, {
        'phase': STANDARD_PHASE, 'message': 'Analysis phase complete',
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    mdb.jobs['Job-13-178x89-NoHole-Journal']._Message(JOB_COMPLETED, {
        'time': 'Tue Oct 15 12:45:07 2019',
        'jobName': 'Job-13-178x89-NoHole-Journal'})
    # Save by Home on 2019_10_15-12.58.48; build 6.14-3 2015_02_02-13.17.19 134785


    # ----------
    mdb.models['Model-1'].boundaryConditions['BC-2'].setValues(ur1=SET, ur2=SET,
        ur3=SET)
    mdb.Job(atTime=None, contactPrint=OFF, description='', echoPrint=OFF,
        explicitPrecision=SINGLE, getMemoryFromAnalysis=True, historyPrint=OFF,
        memory=90, memoryUnits=PERCENTAGE, model='Model-1', modelPrint=OFF,
        multiprocessingMode=DEFAULT, name='Job-12NoHole-178x89',
        nodalOutputPrecision=SINGLE, numCpus=1, numGPUs=0, queue=None,
        resultsFormat=ODB, scratch='', type=ANALYSIS, userSubroutine='', waitHours=
        0, waitMinutes=0)
    mdb.jobs['Job-12NoHole-178x89'].submit(consistencyChecking=OFF)
    mdb.jobs['Job-12NoHole-178x89']._Message(STARTED, {'phase': BATCHPRE_PHASE,
        'clientHost': 'Sara', 'handle': 0, 'jobName': 'Job-12NoHole-178x89'})
    mdb.jobs['Job-12NoHole-178x89']._Message(WARNING, {'phase': BATCHPRE_PHASE,
        'message': '1012 elements are distorted. Either the isoparametric angles are out of the suggested limits or the triangular or tetrahedral quality measure is bad. The elements have been identified in element set WarnElemDistorted.',
        'jobName': 'Job-12NoHole-178x89'})
    mdb.jobs['Job-12NoHole-178x89']._Message(WARNING, {'phase': BATCHPRE_PHASE,
        'message': '2 nodes associated with rigid bodies have boundary conditions prescribed at nodes other than the reference node. These boundary conditions will be transferred to the associated rigid body reference node.The reference nodes and the dependent nodes have been identified in node set WarnNodeOverconBoundRB.',
        'jobName': 'Job-12NoHole-178x89'})
    mdb.jobs['Job-12NoHole-178x89']._Message(WARNING, {'phase': BATCHPRE_PHASE,
        'message': 'Boundary conditions are specified on inactive dof of 763 nodes. The nodes have been identified in node set WarnNodeBCInactiveDof.',
        'jobName': 'Job-12NoHole-178x89'})
    mdb.jobs['Job-12NoHole-178x89']._Message(ODB_FILE, {'phase': BATCHPRE_PHASE,
        'file': 'D:\\Abaqus Work Directory\\Job-12NoHole-178x89.odb',
        'jobName': 'Job-12NoHole-178x89'})
    mdb.jobs['Job-12NoHole-178x89']._Message(COMPLETED, {'phase': BATCHPRE_PHASE,
        'message': 'Analysis phase complete', 'jobName': 'Job-12NoHole-178x89'})
    mdb.jobs['Job-12NoHole-178x89']._Message(STARTED, {'phase': STANDARD_PHASE,
        'clientHost': 'Sara', 'handle': 17100, 'jobName': 'Job-12NoHole-178x89'})
    mdb.jobs['Job-12NoHole-178x89']._Message(STEP, {'phase': STANDARD_PHASE,
        'stepId': 1, 'jobName': 'Job-12NoHole-178x89'})
    mdb.jobs['Job-12NoHole-178x89']._Message(ODB_FRAME, {'phase': STANDARD_PHASE,
        'step': 0, 'frame': 0, 'jobName': 'Job-12NoHole-178x89'})
    mdb.jobs['Job-12NoHole-178x89']._Message(STATUS, {'totalTime': 0.0,
        'attempts': 0, 'timeIncrement': 0.1, 'increment': 0, 'stepTime': 0.0,
        'step': 1, 'jobName': 'Job-12NoHole-178x89', 'severe': 0, 'iterations': 0,
        'phase': STANDARD_PHASE, 'equilibrium': 0})
    mdb.jobs['Job-12NoHole-178x89']._Message(MEMORY_ESTIMATE, {
        'phase': STANDARD_PHASE, 'jobName': 'Job-12NoHole-178x89',
        'memory': 437.0})
    mdb.jobs['Job-12NoHole-178x89']._Message(ODB_FRAME, {'phase': STANDARD_PHASE,
        'step': 0, 'frame': 1, 'jobName': 'Job-12NoHole-178x89'})
    mdb.jobs['Job-12NoHole-178x89']._Message(STATUS, {'totalTime': 0.1,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 1, 'stepTime': 0.1,
        'step': 1, 'jobName': 'Job-12NoHole-178x89', 'severe': 0, 'iterations': 2,
        'phase': STANDARD_PHASE, 'equilibrium': 2})
    mdb.jobs['Job-12NoHole-178x89']._Message(ODB_FRAME, {'phase': STANDARD_PHASE,
        'step': 0, 'frame': 2, 'jobName': 'Job-12NoHole-178x89'})
    mdb.jobs['Job-12NoHole-178x89']._Message(STATUS, {'totalTime': 0.2,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 2, 'stepTime': 0.2,
        'step': 1, 'jobName': 'Job-12NoHole-178x89', 'severe': 0, 'iterations': 1,
        'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-12NoHole-178x89']._Message(ODB_FRAME, {'phase': STANDARD_PHASE,
        'step': 0, 'frame': 3, 'jobName': 'Job-12NoHole-178x89'})
    mdb.jobs['Job-12NoHole-178x89']._Message(STATUS, {'totalTime': 0.3,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 3, 'stepTime': 0.3,
        'step': 1, 'jobName': 'Job-12NoHole-178x89', 'severe': 0, 'iterations': 1,
        'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-12NoHole-178x89']._Message(ODB_FRAME, {'phase': STANDARD_PHASE,
        'step': 0, 'frame': 4, 'jobName': 'Job-12NoHole-178x89'})
    mdb.jobs['Job-12NoHole-178x89']._Message(STATUS, {'totalTime': 0.4,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 4, 'stepTime': 0.4,
        'step': 1, 'jobName': 'Job-12NoHole-178x89', 'severe': 0, 'iterations': 1,
        'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-12NoHole-178x89']._Message(ODB_FRAME, {'phase': STANDARD_PHASE,
        'step': 0, 'frame': 5, 'jobName': 'Job-12NoHole-178x89'})
    mdb.jobs['Job-12NoHole-178x89']._Message(STATUS, {'totalTime': 0.5,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 5, 'stepTime': 0.5,
        'step': 1, 'jobName': 'Job-12NoHole-178x89', 'severe': 0, 'iterations': 1,
        'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-12NoHole-178x89']._Message(ODB_FRAME, {'phase': STANDARD_PHASE,
        'step': 0, 'frame': 6, 'jobName': 'Job-12NoHole-178x89'})
    mdb.jobs['Job-12NoHole-178x89']._Message(STATUS, {'totalTime': 0.6,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 6, 'stepTime': 0.6,
        'step': 1, 'jobName': 'Job-12NoHole-178x89', 'severe': 0, 'iterations': 1,
        'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-12NoHole-178x89']._Message(ODB_FRAME, {'phase': STANDARD_PHASE,
        'step': 0, 'frame': 7, 'jobName': 'Job-12NoHole-178x89'})
    mdb.jobs['Job-12NoHole-178x89']._Message(STATUS, {'totalTime': 0.7,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 7, 'stepTime': 0.7,
        'step': 1, 'jobName': 'Job-12NoHole-178x89', 'severe': 0, 'iterations': 1,
        'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-12NoHole-178x89']._Message(ODB_FRAME, {'phase': STANDARD_PHASE,
        'step': 0, 'frame': 8, 'jobName': 'Job-12NoHole-178x89'})
    mdb.jobs['Job-12NoHole-178x89']._Message(STATUS, {'totalTime': 0.8,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 8, 'stepTime': 0.8,
        'step': 1, 'jobName': 'Job-12NoHole-178x89', 'severe': 0, 'iterations': 1,
        'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-12NoHole-178x89']._Message(ODB_FRAME, {'phase': STANDARD_PHASE,
        'step': 0, 'frame': 9, 'jobName': 'Job-12NoHole-178x89'})
    mdb.jobs['Job-12NoHole-178x89']._Message(STATUS, {'totalTime': 0.9,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 9, 'stepTime': 0.9,
        'step': 1, 'jobName': 'Job-12NoHole-178x89', 'severe': 0, 'iterations': 1,
        'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-12NoHole-178x89']._Message(ODB_FRAME, {'phase': STANDARD_PHASE,
        'step': 0, 'frame': 10, 'jobName': 'Job-12NoHole-178x89'})
    mdb.jobs['Job-12NoHole-178x89']._Message(STATUS, {'totalTime': 1.0,
        'attempts': 1, 'timeIncrement': 0.1, 'increment': 10, 'stepTime': 1.0,
        'step': 1, 'jobName': 'Job-12NoHole-178x89', 'severe': 0, 'iterations': 1,
        'phase': STANDARD_PHASE, 'equilibrium': 1})
    mdb.jobs['Job-12NoHole-178x89']._Message(END_STEP, {'phase': STANDARD_PHASE,
        'stepId': 1, 'jobName': 'Job-12NoHole-178x89'})
    mdb.jobs['Job-12NoHole-178x89']._Message(COMPLETED, {'phase': STANDARD_PHASE,
        'message': 'Analysis phase complete', 'jobName': 'Job-12NoHole-178x89'})
    mdb.jobs['Job-12NoHole-178x89']._Message(JOB_COMPLETED, {
        'time': 'Tue Oct 15 13:32:20 2019', 'jobName': 'Job-12NoHole-178x89'})
    # Save by Home on 2019_10_15-14.20.50; build 6.14-3 2015_02_02-13.17.19 134785
